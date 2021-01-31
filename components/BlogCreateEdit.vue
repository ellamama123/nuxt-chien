<template>
    <div>
                        <div class="form-group">
                            <label for="exampleFormControlInput1">Tiêu đề</label>
                            <input type="text" class="form-control" placeholder="" v-validate="{ required: true }" v-model="form.title" >
                        </div>
                        <div class="form-group">
                            <label for="exampleFormControlInput1">Mô tả nguồn</label>
                            <input type="text" class="form-control" placeholder="" v-model="form.des">
                        </div>
                        <div class="form-group">
                            <p for="exampleFormControlTextarea1">Chi tiết</p>
                            <textarea class="form-control" rows="5" v-model="form.detail"></textarea>
                        </div>
                        <div class="form-group">
                            <p for="exampleFormControlFile1">Hình ảnh</p>
                            <input type="text" class="form-control" v-model="form.thumbs">
                        </div>

                        <div class="form-group">
                            <p class="mr-sm-2" for="inlineFormCustomSelect">Loại</p>
                            <select class="custom-select mr-sm-2" v-if="this.$route.name =='add'" v-model="form.category">
                                <option v-for="(categ,index) in DATA_CATE" v-bind:key="categ" :value=" index" > {{ categ }} </option>
                            </select>
                            <select class="custom-select mr-sm-2" v-else v-model="form.category">
                                <option v-for="(categ,index) in DATA_CATE" v-bind:key="categ" :value=" index" > {{ categ }} </option>
                            </select>

                        </div>
                        <div class="form-group">
                            <p>Vị trí</p>
                            <ul class="list-group list-group-flush">
                                <li
                                v-for="(pos, index) in DATA_POS"
                                v-bind:key="pos"
                                class="list-group-control"
                                >
                                <div class="custom-control custom-checkbox">
                                    <input
                                    type="checkbox"
                                    class="custom-control-input"
                                    :id="index + 'custom'"
                                    :value="index"
                                    name="vietnam"
                                    v-model="form.position"
                                    >
                                    <label
                                    class="custom-control-label"
                                    :for="index + 'custom'"
                                    >{{ pos }}</label>
                                </div>
                                </li>
                            </ul>
                        </div>
                        <div class="form-group">
                            <label class="bold">Public</label><br>
                            <input type="radio" id="checkbox1" :name="yes" :value="true" v-model="form.public">
                            <label for="checkbox1">Yes</label><br>
                            <input type="radio" id="checkbox2" :name="no" :value="false" v-model="form.public">
                            <label for="checkbox2">No</label><br>
                        </div>
                        <div class="form-group ">
                            <p for="example-datetime-local-input" class="col-form-label">Date</p>
                            <div class="">
                                <input class="form-control" type="date" value="2011-08-19" id="example-datetime-local-input" v-model="form.data_pubblic">
                            </div>
                        </div>
                        <p v-if="errors.length">
                            <b>Lỗi:</b>
                            <ul>
                            <li v-for="error in errors" v-bind:key="error"><p class="alert alert-warning">{{ error }}</p></li>
                            </ul>
                        </p>
                        <div class="form-group button">
                            <button type="button" class="btn btn-success" v-if="this.$route.name =='blog-add'" @click="submit"><a href="/blog">Add</a></button>
                             <button type="button" class="btn btn-success" v-else @click="update">Update</button>
                            <button type="button" class="btn btn-primary">Clear</button>
                        </div>
    </div>
</template>
<script>
import { DATA_CATE } from '@/store/const.js'
import { DATA_POS } from '@/store/const.js'
import axios from "axios";
export default {
    data(){
        return {
            DATA_CATE: DATA_CATE,
            DATA_POS: DATA_POS,
            form: {
                'title' : '',
                'des' : '',
                'detail' : '',
                'public' : '',
                'data_pubblic' : '',
                'thumbs':''
            },
            errors : [],
        }
    },
    created() {
        console.log(this.$route.name)
    }
    ,
    mounted() {
        if(this.$route.name != 'blog-add')
            this.list()
    },
    computed: {
        dataCate: function () {
        return this.DATA_CATE
        },
        dataPos: function () {
        return this.DATA_POS
        }
    },
    methods: {
        submit(){
            this.errors = []
            if(!this.form.title) this.errors.push("Tiêu đề trống")
            if(!this.form.des) this.errors.push("Mô tả trống")
            if(!this.form.detail) this.errors.push("Chi tiết trông trống")
            if(!this.form.data_pubblic) this.errors.push("Ngày trống")
            if(!this.form.position) this.errors.push("Vị trí trống")
            if(!this.form.thumbs) this.errors.push("Ảnh trống")
            if(this.errors.length > 0) return false
            axios.post('http://127.0.0.1:8000/api/blog', this.form)
            .then(function( response ){});  
            console.log(this.form);
            this.$router.push({ path: '/' })

        },

        list(){
            axios.get('http://127.0.0.1:8000/api/blog/' + this.$route.params.id) .then((result) => {
            this.form = result.data; 
            })
            
        },

        update(){
            this.errors = []
            if(!this.form.title) this.errors.push("Tiêu đề trống")
            if(!this.form.des) this.errors.push("Mô tả trống")
            if(!this.form.detail) this.errors.push("Chi tiết trông trống")
            if(!this.form.data_pubblic) this.errors.push("Ngày trống")
            if(!this.form.position) this.errors.push("Vị trí trống")
            if(!this.form.thumbs) this.errors.push("Ảnh tin trống")
            if(this.errors.length > 0) return false
            axios.put('http://127.0.0.1:8000/api/blog/' + this.$route.params.id, this.form)
            .then(function( response ){
                }.bind(this));
            this.$router.push({ path: '/' })
        }
        },
}
</script>

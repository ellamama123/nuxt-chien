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
                            <select class="custom-select mr-sm-2" v-model="form.category">
                                <option v-for="(categ,index) in cate" v-bind:key="categ" :value=" index"> {{ categ }} </option>
                            </select>
                        </div>
                        <div class="form-group">
                            <p>Vị trí</p>
                            <ul class="list-group list-group-flush">
                                <li v-for="(post,index) in pos" v-bind:key="post"  class="list-group-control">
                                    <div class="custom-control custom-checkbox">
                                        <input type="checkbox" name="vietnam" :value="index-1" class="custom-control-input" :id="index+'a'" v-model="form.position">
                                        <label class="custom-control-label" :for="index+'a'">{{ post }}</label>
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
                            <button type="button" class="btn btn-success" v-if="this.$route.name =='add'" @click="submit"><a href="/">Submit</a></button>
                             <button type="button" class="btn btn-success" v-else @click="update">Submit</button>
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
                'id': '',
                'title' : '',
                'des' : '',
                'detail' : '',
                'category' : '',
                'public' : '',
                'data_pubblic' : '',
                'position' : [],
                'thumbs':''
            },
            errors : [],
        }
    },
    mounted() {
        console.log(this.cate)
        if(this.$route.name != 'add')
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
            if(!this.form.category) this.errors.push("Danh mục trống")
            if(!this.form.data_pubblic) this.errors.push("Ngày trống")
            if(!this.form.position) this.errors.push("Vị trí trống")
            if(!this.form.thumbs) this.errors.push("Ảnh trống")
            if(this.errors.length > 0) return false
            axios.post('http://localhost:4000/blogs/', this.form)
            .then(function( response ){});  
            this.$router.push({ path: '/' })

        },

        list(){
            axios.get('http://localhost:4000/blogs/' + this.$route.params.id) .then((result) => {
            this.form = result.data; 
            })
            
        },

        update(){
            this.errors = []
            if(!this.form.title) this.errors.push("Tiêu đề trống")
            if(!this.form.des) this.errors.push("Mô tả trống")
            if(!this.form.detail) this.errors.push("Chi tiết trông trống")
            if(!this.form.category) this.errors.push("Danh mục trống")
            if(!this.form.data_pubblic) this.errors.push("Ngày trống")
            if(!this.form.position) this.errors.push("Vị trí trống")
            if(!this.form.thumbs) this.errors.push("Ảnh tin trống")
            if(this.errors.length > 0) return false
            axios.put('http://localhost:4000/blogs/' + this.$route.params.id, this.form)
            .then(function( response ){
                }.bind(this));
            this.$router.push({ path: '/' })
        }
        },
}
</script>

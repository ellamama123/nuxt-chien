<template>
    <div>
                        <div class="form-group">
                            <label for="exampleFormControlInput1">Tiêu đề</label>
                            <input type="text" class="form-control" placeholder="" v-model="form.title">
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
                            <input type="file" class="form-control-file" v-on:change="form.thumbs">
                        </div>

                        <div class="form-group">
                            <p class="mr-sm-2" for="inlineFormCustomSelect">Loại</p>
                            <select class="custom-select mr-sm-2" v-model="category">
                                <option selected value="0">Thời sự</option>
                                <option value="1">Thể thao</option>
                                <option value="2">Văn hóa</option>
                                <option value="3">Nghệ thuật</option>
                            </select>
                        </div>
                        <div class="form-group">
                            <p>Vị trí</p>
                            <ul class="list-group list-group-flush">
                                <li class="list-group-control">
                                    <div class="custom-control custom-checkbox">
                                        <input type="checkbox" name="vietnam" value="1" class="custom-control-input" id="customCheck1" v-model="form.position">
                                        <label class="custom-control-label" for="customCheck1">Việt Nam</label>
                                    </div>
                                </li>
                                <li class="list-group-control">
                                    <div class="custom-control custom-checkbox">
                                        <input type="checkbox" name="chaua" value="2" class="custom-control-input" id="customCheck2" v-model="form.position">
                                        <label class="custom-control-label" for="customCheck2">Châu Âu</label>
                                    </div>
                                </li>
                                <li class="list-group-control">
                                    <div class="custom-control custom-checkbox">
                                        <input type="checkbox" name="chauau" value="3" class="custom-control-input" id="customCheck3" v-model="form.position">
                                        <label class="custom-control-label" for="customCheck3">Châu Á</label>
                                    </div>
                                </li>
                                <li class="list-group-control">
                                    <div class="custom-control custom-checkbox">
                                        <input type="checkbox" name="chaumy" value="4" class="custom-control-input" id="customCheck5" v-model="form.position" >
                                        <label class="custom-control-label" for="customCheck5">Châu Mỹ</label>
                                    </div>
                                </li>
                            </ul>
                        </div>
                        <div class="form-group">
                                <p>Public</p>
                                <div class="">
                                    <div class="custom-control custom-radio">
                                        <input type="radio" id="customRadio1"  name="customRadio1" value="true" class="custom-control-input" checked v-model="form.public">
                                        <label class="custom-control-label" for="customRadio1">Yes</label>
                                    </div>
                                    <div class="custom-control custom-radio">
                                        <input type="radio" id="customRadio2" name="customRadio2" value="false" class="custom-control-input" v-model="form.public">
                                        <label class="custom-control-label" for="customRadio2">No</label>
                                    </div>
                                </div>
                        </div>
                        <div class="form-group ">
                            <p for="example-datetime-local-input" class="col-form-label">Date</p>
                            <div class="">
                                <input class="form-control" type="datetime-local" value="2011-08-19T13:45:00" id="example-datetime-local-input" v-model="form.datapublic">
                            </div>
                        </div>
                        <div class="form-group button">
                            <button type="button" class="btn btn-success" @click="submit">Submit</button>
                            <button type="button" class="btn btn-primary">Clear</button>
                        </div>
    </div>
</template>
<script>
import axios from "axios";
export default {
    data(){
        return {
            form: {
                'id': '',
                'title' : '',
                'des' : '',
                'detail' : '',
                'category' : '',
                'public' : '',
                'data-public' : '',
                'position' : [],
                'thumbs':''
            }
        }
    },

    methods: {
        isChecked(index) {
            return this.availableRoles[index].id === this.user.roles[index].id
        },
        submit(){
            axios.post('http://localhost:4000/blogs/', this.form)
                .then(function( response ){
                    // Handle success
                }.bind(this));
        }
    },
}
</script>

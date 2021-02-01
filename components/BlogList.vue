<template lang="">
                   
        <table class="table table-hover table-bordered">
            <thead class="thin-border-bottom">
                <tr>
                    <th>ID</th>
                    <th>Tin</th>
                    <th>Loại</th>
                    <th>Trạng thái</th> 
                    <th>Vị trí</th>
                    <th>Ngày Public</th>
                    <th>Edit</th>
                    <th>Delete</th>     
                </tr>
            </thead>
            
            <tbody v-if="blogs && blogs.length">
                <tr v-for="(blog,index) of blogs" v-bind:key="blog.id" v-bind:title="blog.title">
                    <td>{{blog.id}}</td>
                    <td>{{blog.title}}</td>
                    <td>
                        <div
                        v-for="(cate, index) in dataCate"
                        :key="index"
                        >
                        <p v-if="index == blog.category">{{cate}}</p>

                        </div>
                    </td>
                    <td v-if="blog.public == true ">Yes</td>
                    <td v-if="blog.public == false ">No</td>
                    <td>
                            <p>{{parseJSONIfJSON(blog.position)}}</p>
                    </td>
                    <td>{{blog.data_pubblic}}</td>
                    <td><button type="button" class="btn btn-primary"><a v-bind:href="'/blog/'+ blog.id" title="">Edit</a></button></td>
                    <td><button type="button" class="btn btn-danger" v-on:click="fireDelete(blog.id, index)">Delete</button></td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
import { DATA_CATE } from '@/const/const.js'
import { DATA_POS } from '@/const/const.js'
import axios from "axios";
export default {
    props:['blogs'],
    data() {
        return {
        DATA_CATE,
        DATA_POS,
        }
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
        fireDelete(id, index) {      
            if(confirm("Bạn có chắc chắn muốn xóa không ?")){
            axios.delete('http://127.0.0.1:8000/api/blog/'+id).then((res) => {
                this.blogs.splice(index, 1);
            }) 
            }   
        },

        parseJSONIfJSON(posit) {
            try {
                const posArr = JSON.parse(posit)
                return posArr.join(', ')
            } catch (error) {
                return ""
            }
        }
    }
}

</script>

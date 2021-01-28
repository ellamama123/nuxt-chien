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
                    <td v-if="blog.category == 0">Thời sự</td>
                    <td v-else-if="blog.category == 1">Thể thao</td>
                    <td v-else-if="blog.category == 2">Văn hóa</td>
                    <td v-else-if="blog.category == 3">Nghệ thuật</td>
                    <td v-else>Chính trị</td>
                    <td v-if="blog.public === false">Không hiển thị</td>
                    <td v-else-if="blog.public === true">Hiển thị</td>
                    <td>
                        <ul>
                            <div v-for="position of blog.position" >
                                <li v-if="position == 1"> Hà Nội</li>
                                <li v-if="position == 2"> Châu Âu</li>
                                <li v-if="position == 3"> Châu Á</li>
                                <li v-if="position == 4"> Châu Mỹ</li>
                            </div>
                        </ul>
                        
                    </td>
                    <td>{{blog.data_pubblic}}</td>
                    <td><button type="button" class="btn btn-primary"><a v-bind:href="'/edit/'+ blog.id" title="">Edit</a></button></td>
                    <td><button type="button" class="btn btn-danger" v-on:click="fireDelete(blog.id, index)">Delete</button></td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>

import axios from "axios";
export default {
    props:['blogs'],
    methods: {       
        fireDelete(id, index) {      
            console.log(index),
            axios.delete('http://localhost:4000/blogs/'+id).then((res) => {
                this.blogs.splice(index, 1);
            })    
        },    
    }
}

</script>

<template lang="">
      <div>
          <h1>Search Blog</h1>
            <div class="row">
                <div class="col-md-3">
                    <p>Tiêu đề</p>
                </div>
                <div class="col-md-9">
                    <input type="text" name="title" class="form-control" v-model="search" />
                </div>
            </div>
            <div class="row">
                <div class="col-md-12">
                    <button class="btn btn-success search" @click="searchBlog(search)" >Search</button>
                </div>
            </div>
            <blog-list :blogs="blogs"></blog-list>
      </div>
</template>
<script>
import axios from 'axios'
export default {
  data () {
      return {
          search : '',
          blogs:[]
      }  
  },
  mounted() {
    this.searchBlog(this.search)
  },
  methods: {
    searchBlog: function(search = '') {
      const url = search ? 'http://127.0.0.1:8000/api/blog?title=' + search : 'http://127.0.0.1:8000/api/blog/';
                axios.get(url)
                .then(response => {
                this.blogs = response.data
            })
    }
  },
}
</script>

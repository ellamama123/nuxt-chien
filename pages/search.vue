
<template lang="">
    
    <div class="form-control">
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
                    <button class="btn btn-success search" @click="search1(search)" >Search</button>
                </div>
            </div>
        <blog-list :blogs="blogs"></blog-list>
    </div>
    
</template>
<script>
import BlogList from '@/components/BlogList.vue'
import axios from 'axios'
export default {
  components: { BlogList },
  data () {
      return {
          search : '',
          blogs:[]
      }  
  },
  mounted() {
    this.search1(this.search)
  },
  methods: {
    search1: function(search = '') {
      const url = search ? 'http://localhost:4000/blogs?title_like=' + search : 'http://localhost:4000/blogs';
                axios.get(url)
                .then(response => {
                this.blogs = response.data
            })
    }
  },

}
</script>

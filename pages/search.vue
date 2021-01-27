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
                    <button class="btn btn-success search" @click="searchPost" >Search</button>
                </div>
            </div>
        <blog-list ref="list"></blog-list>
    </div>
    
</template>
<script>
import BlogList from '@/components/BlogList.vue'

export default {
  components: { BlogList },
  data () {
      return {
          search : '',
      }  
  },
  methods : {
      searchPost(){
          console.log(this.$refs)
          this.$refs.list.search(this.search);
      }
  }

}
</script>

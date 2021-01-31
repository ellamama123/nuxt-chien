<template>
  <div>
    <h1>Inex Blog</h1>
    <blog-list :blogs="blogs" />
  </div>
</template>

<script>
import BlogList from '@/components/BlogList.vue'
import axios from 'axios'
export default {
  components: { BlogList },
  data() {
    return {
      blogs : []   
   }
  },
  mounted() {
    this.show()
  },
  methods: {
    show: function() {
      const url =  'http://127.0.0.1:8000/api/blog'
      axios.get(url).then((response) => {
        this.blogs = response.data
      })
    },
  },
}
</script>

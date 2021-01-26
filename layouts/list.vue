<template >
  <div>
    <app-header></app-header>
    <div class="menu">
        <div class="container">
            <div class="row">
                <div class="col-md-3">
                  <app-menu></app-menu>
                </div>
                 <div class="col-md-9">
                   <blog-list></blog-list>
                </div>
            </div>
        </div>

    <app-footer></app-footer>
    
  </div>
  </div>
</template>
<script>
import AppHeader from '@/components/AppHeader'
import AppMenu from '@/components/AppMenu.vue'
import AppFooter from '@/components/AppFooter.vue'
import BlogList from '@/components/BlogList.vue'
export default {
  components: {
    AppHeader,AppMenu,AppFooter,BlogList
    
  }
}
</script>

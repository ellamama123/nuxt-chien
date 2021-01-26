<template lang="">
    <div>
    <app-header></app-header>
    <div class="menu">
        <div class="container">
            <div class="row">
                <div class="col-md-3">
                  <app-menu></app-menu>
                </div>
                 <div class="col-md-9">
                     <div class="form-control">
                        <form action="">
                            <div class="row">
                                <div class="col-md-3">
                                    <p>Tiêu đề</p>
                                </div>
                                <div class="col-md-9">
                                    <input type="text" name="title" class="form-control" />
                                </div>
                            </div>
                            <div class="row">
                                <button>Search</button>
                            </div>
                        </form>
                    </div>
                   <blog-list></blog-list>
                </div>
            </div>
        </div>
    </div>
    <app-footer></app-footer>
    
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
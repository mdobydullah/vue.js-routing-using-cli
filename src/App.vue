<template>
  <div id="app" class="container">
    <nav class="navbar navbar-expand-lg navbar-light" style="background-color: #e3f2fd;">
      <div class="collapse navbar-collapse" id="navbarTogglerDemo03">
        <ul class="navbar-nav mr-auto mt-2 mt-lg-0">
        <li> <router-link class="nav-link" to="/"> Home </router-link> </li>
        <li> <router-link class="nav-link" to="about"> About </router-link> </li>
        <li> <router-link class="nav-link" to="contact"> Contact </router-link> </li>
        </ul>
      </div>
    </nav>
    <div class="text-center" style="margin-top: 20px;">
      <router-view></router-view>
    </div>
  </div>
</template>

<script>
import Vue from 'vue'
import VueRouter from 'vue-router'

Vue.use(VueRouter)

import Home from './components/Home.vue'
import About from './components/About.vue'
import Contact from './components/Contact.vue'

const router = new VueRouter({
  mode: 'history',
  base: __dirname,
  routes: [
    { path: '/', component: Home, meta:{title: 'Home'} },
    { path: '/about', component: About, meta:{title: 'About'} },
    { path: '/contact', component: Contact, meta:{title: 'Contact'} }
  ]
})

// set dynamic meta title
router.beforeEach((to, from, next) => {
  document.title = to.meta.title
  next()
});

export default {
  name: 'app',
  router
}
</script>

<style>
#app {
  text-align: center;
  margin-top: 50px;
}
</style>
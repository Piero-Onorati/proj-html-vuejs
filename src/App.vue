<template>
  <div id="app">
    <!-- TOP NAVBAR -->
    <TopNavbar/>
    <!-- NAVBAR -->
    <Navbar/>
    <Header/>
    <MainContent/>
    <Footer/>
  </div>
</template>

<script>
import TopNavbar from '@/components/TopNavbar.vue'
import Navbar from '@/components/Navbar.vue'
import Header from '@/components/Header.vue';
import MainContent from '@/components/MainContent.vue';
import Footer from '@/components/Footer.vue'

export default {
  name: 'App',
  components: {
    TopNavbar,
    Navbar,
    Header,
    MainContent,
    Footer
    
  }
}
</script>

<style lang="scss">
@import 'style/commons.scss';
@import 'style/framework.scss';


</style>

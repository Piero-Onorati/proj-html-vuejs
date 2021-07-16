<template>

  <header>

    <!-- TOP NAVBAR -->
    <TopNavbar/>

    <!-- NAVBAR -->
    <Navbar/>

    <!-- start THIN DIVIDER -->
    <div class="thin-divider">

      <div class="container">
        <!-- first item-divider -->
        <div class="item-divider">
          <i class="far fa-map"></i>
          <div class="item-divider-description"><strong>International</strong>Shipping Services</div>
        </div>

        <!-- secnd item-divider -->
        <div class="item-divider">
          <i class="far fa-clock"></i>
          <div class="item-divider-description">See our <strong>store hours and</strong> services</div>
        </div >

        <!-- third item-divider -->
        <div class="item-divider">
          <i class="fas fa-check"></i>
          <div class="item-divider-description">We price match to give you the <strong>best deals</strong></div>
        </div>
      </div>

    </div>
    <!-- end THIN DIVIDER -->

    <!-- start Jumbotron -->
    <div class="jumbotron">
      <div class="overlay"></div>
    </div>
    <!-- end Jumbotron -->

    <!-- start LARGE DIVIDER -->
    <div class="large-divider">
      <img src="../assets/img/food-transparent-5.png" alt="animal-food">
      <h2>Get $25 OFF your first purchase of our homemade pet food!</h2>
      <a href="#">Visit the shop</a>
    </div>
    <!-- end LARGE DIVIDER -->
    
  </header>

</template>

<script>
import TopNavbar from '@/components/TopNavbar.vue'
import Navbar from '@/components/Navbar.vue'


export default {
    name: 'Header',
    components:{
      TopNavbar,
      Navbar
    }

}
</script>

<style lang='scss'>
@import '../style/mixins.scss';
@import '../style/vars.scss';

.thin-divider{
  @include green-paw;
  padding: 20px 0;

  .container{
    @include flex-around;
    color:white;
    font-size:14px ;

    .item-divider{
      @include flex-cc;

      .item-divider-description{
        font-size: 16px;
        padding-left: 8px;
      }
    }
  }
}

.jumbotron{
  height: 580px;
  background-image: url('../assets/img/banner-5-2x-scaled.jpg');
  background-size: cover;
  background-position: center;

  .overlay{
    width: 100%;
    height: 100%;
    background-color: rgba(0,0,0,0.3);
  }
}

.large-divider{
  @include flex-cc;
  @include green-paw;
  padding-top:20px ;

  img{
    width:13%
  }
}

</style>
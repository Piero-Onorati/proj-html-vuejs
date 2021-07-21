<template>

  <header>
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
      <div class="overlay">
        <div class="container">
          <div class="box">
              <span>find the best animals supplies</span>
              <h2>We know animals are a part of your family, let us help take care of them.</h2>  
              <button>Learn more about us</button>
            
          </div>
        </div>

      </div>
    </div>
    <!-- end Jumbotron -->

    <!-- start LARGE DIVIDER -->
    <div class="large-divider">
      <img src="../assets/img/food-transparent-5.png" alt="animal-food">
      <h3>Get $25 OFF your first purchase of our homemade pet food!</h3>
      <a href="#">Visit the shop</a>
    </div>
    <!-- end LARGE DIVIDER -->
    
  </header>

</template>

<script>

export default {
  name: 'Header',
  components:{
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
    @include flex-cc;
    width: 100%;
    height: 100%;
    background-color: rgba(0,0,0,0.3);

    .box{
      height: 100%;
      width: 100%;
      text-align: left;
      span{
        @include span-banner;
      }

      h2{
        @include h2-banner;
        width:50%

      }

      button{
      @include white-button;

      }
    }
  }
}

.large-divider{
  @include flex-cc;
  @include green-paw;
  padding-top:20px ;
  
  img{
    width:13%
  }

  h3{
    color:white;
    font-weight:400;
    font-size:22px;
    padding: 0 30px;
  }

  a{
    color:$salvia-green;
    font-size:20px;

    &:hover{
      color: white;
    }
  }

  &.sticky{
    position: sticky;
    top: 0;
    width: 100%;
  }
  
}

</style>
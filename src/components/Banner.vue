<template>
  <div class="banner">
    <div class="overlay">
      <div class="text">
        <span>find the best animals supplies</span>
        <h2>New arrivals weekly</h2>  
        <button>Learn more about us</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
    name:'Banner'

}
</script>

<style lang="scss" scoped>
@import '../style/mixins.scss';
@import '../style/vars.scss';

.banner{
  @include flex-cc;
  flex-direction: column;
  background-image: url('../assets/img/banners/banner-1.jpg');
  background-size: cover;
  background-position: center;
  height: 550px;
  width: 100%;

  .overlay{
    @include flex-cc;
    width: 100%;
    height: 100%;
    background-color: rgba(0,0,0,0.2);
    .text{
      text-align: center;

      span{
        @include span-banner;
      }

      h2{
        @include h2-banner;
      }

      button{
      @include white-button;

      }
    }
    
  }

}




</style>
<template>
  <div class="banner fade-in">

    <div class="overlay">

      <!-- Start content -->
      <div class="text">

        <!-- Title -->
        <h2>Join our newsletter</h2>  

        <!-- Section-description -->
        <p>Volutpat vel turpis nulla lorem sed semper. Aliquam sagittis sem libero viverra vehicula nullam ut nisl.</p>

        <!-- Input -->
        <div class="newsletter-box">
            <div class="input-box">
                <input type="mail" placeholder="Insert your email...">
            </div>
            <button>Subscribe</button>
        </div>

      </div>
      <!-- End content -->

    </div>
  </div>
</template>

<script>
export default {
  name:'BannerNewsL',
}
</script>

<style lang="scss" scoped>
@import '../style/mixins.scss';
@import '../style/vars.scss';


.banner{
  @include flex-cc;
  background-image:  url('../assets/img/banners/banner-2.jpg');
  background-size: cover;
  background-position: center;
  height: 500px;
  width: 100%;
  margin-top:-100px;
  
  .overlay{
    @include flex-start-center;
    width: 100%;
    height: 100%;
    background:linear-gradient(#f8f5f200, #f8f5f267);

    .text{
      text-align: left;
      padding-left: 100px;

      h2{
        font-size:$fsize-heading-big-title;
        font-family: "Trocchi";
        font-weight: 300;
        color: $dark-green;
      }

      p{
        @include p-heading;
        padding: 40px 0;
      }

      .newsletter-box{
        @include flex-between;
        width:80%;

        .input-box{
          background-color: $sand;
          border-radius: 30px;
          width:350px;
          padding: 22px 10px;

          input{
            background-color: transparent;
            border:none;
            padding-left: 8px;
            font-size: $fsize-input-placeholder;

            &::placeholder{
              font-size: $fsize-input-placeholder;
              font-family: 'Work Sans';
            }
          }
        }

        button{
          @include green-button-input
        }

      }
    }
  }
}

</style>
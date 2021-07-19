<template>
  <div div class="banner">
    <div class="overlay">

      <div class="text">
        <h2>Join our newsletter</h2>  
        <p>Volutpat vel turpis nulla lorem sed semper. Aliquam sagittis sem libero viverra vehicula nullam ut nisl.</p>
        <div class="newsletter-box">
            <div class="input-box">
                <input type="mail">
            </div>
            <button>Subscribe</button>
        </div>

      </div>
    </div>
    
    
  </div>
</template>

<script>
export default {

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
        background:linear-gradient(#f8f5f200, #f8f5f25b);

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
            background-color: #f8f5f2;
            width: 350px;
            border-radius: 30px;
            padding: 14px 10px;
                input{
                    background-color: transparent;
                    border:none
                }
            }
    
            button{
                background-color: $green;
                color: white;
                font-size: $fsize-heading-span;
                font-weight: $fweight-medium;
                font-family: 'Work Sans';
                border-radius: 30px;
                border:none;
                padding:20px 60px;
                cursor: pointer;
    
                &:hover {
                background-color: darken($green, 8%);
                }
            }
    
          }
    
        }
    }

}

</style>
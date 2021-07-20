<template>
<footer>
  <div class="container">

    <!-- start ROW-1, composed by 4 COL -->
    <div class="row row-1">

      <!-- FIRST COL: LOGO + ADRESS -->
      <div class="col-xs-3">

        <!-- logo -->
        <div class="logo">
          <img src="../assets/img/logo-footer.png" alt="logo-footer">
        </div>

        <!-- adress -->
        <div class="adress">
          <span>1234 Avada Avenue Avadaville</span>
          <span>info@your-company.com</span>
          <span>Call us: (1) 234 5678</span>
        </div>

      </div>

      <!-- SECOND COL -->
      <div class="col-xs-3">
        <ul>
          <li>Shop By Brand</li>
          <li v-for="(link,index) in shopByBrand" :key="index"><a :href="link.url">{{link.name}}</a></li>
        </ul>
      </div>

      <!-- THIRD COL -->
      <div class="col-xs-3">
        <ul>
          <li>Useful Links</li>
          <li v-for="(link,index) in usefulLinks" :key="index"><a :href="link.url">{{link.name}}</a></li>
        </ul>
      </div>

      <!-- FOURTH COL: SUBSCRIBE NEWSLETTER -->
      <div class="col-xs-3 news-col">
        <div class="newsletter">
          <div class="overlay">

            <!-- subscribe title -->
            <h3>Subscribe to our newsletter</h3>

            <!-- input-box -->
            <div class="input-box">
                <input type="mail" placeholder="Insert your email...">
            </div>

            <!-- button subscribe -->
            <button>Subscribe</button>

          </div>
        </div>
      </div>
    </div>
    <!-- end ROW-1, composed by 4 COL -->

    <!-- start FOOTER-NAV -->
    <div class="row footer-nav">
      <div class="col-xs-12">
        <ul>
          <li v-for="(link,index) in footerNav" :key="index"><a :href="link.url" :class="{ active:link.selected }">{{link.link}}</a></li>
        </ul>
      </div>
    </div>
    <!-- end FOOTER-NAV -->

    <!-- start ROW-2: SOCIALS ICONS -->
    <div class="row row-2">
      <div class="col-xs-12 social-icons">
        <i class="fab fa-facebook-f social-i"></i>
        <i class="fab fa-twitter social-i"></i>
        <i class="fab fa-instagram social-i"></i>
        <i class="fab fa-youtube social-i"></i>
      </div>
    </div>
    <!-- end ROW-2: SOCIALS ICONS -->

  </div>

</footer>
</template>

<script>
import FooterNav from '@/data/FooterNav.js';
import ShopByBrand from '@/data/ShopByBrand.js';
import UsefulLinks from '@/data/UsefulLinks.js';


export default {
  name:'Footer',
  data(){
    return{
      shopByBrand:ShopByBrand,   
      usefulLinks:UsefulLinks,
      footerNav:FooterNav
    }
  }


}
</script>

<style lang="scss" scoped>
@import '../style/mixins.scss';
@import '../style/vars.scss';

footer{
  background-color: #1e3120;
  .container{
    
    .row-1{
      padding: 100px 25px 50px 25px;
      border-bottom:1px solid $salvia-green;

      .logo{
        width:250px;
        img{
          width: 100%;
        }
      }
  
      .adress{
        padding-top: 35px;
        span{
          display: block;
          color: white;
          font-size: $fsize-footer-small;
          font-weight: 300px;
          line-height: 36px;
        }
      }
  
      ul{
        li{
          list-style: none;
          font-size:$fsize-footer-big ;
          color: white;
           padding: 15px 0;
          a{
            text-decoration: none;
            color: white;
            font-size: $fsize-footer-small ;
            transition: 0.2s ease-in-out;

            &:hover{
              color:$salvia-green;
            }
          }
        }
      }
  
      .news-col{
        @include flex-cc;
        .newsletter{
          background-color: #264229;
          padding: 20px 40px;
          background-image: url('../assets/img/bg-transparent-3.png');
          height: 350px;
          width:320px;
          border-radius:10px;
          overflow: hidden;
          .overlay{
            @include flex-around;
            flex-direction: column;
            width: 100%;
            height: 100%;
            background-image: linear-gradient(#26422900,#264229);

            h3{
              color:white;
              font-size:$fsize-footer-big;
              letter-spacing: 1px;
              line-height: 34px;
              font-weight: 400;
            }
  
            .input-box{
              background-color: $sand;
              border-radius: 30px;
              width:100%;
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
              @include green-button-input;
              width:100%;
            }
          }
        
        }
  
      }
  
    }

    .footer-nav{
      padding-top:80px;
      @include flex-cc;
      ul{
        @include flex-cc;
        li{
          list-style: none;
          margin: 0 15px;
          a{
            font-size: $fsize-footer-small;
            color: $salvia-green;
            text-decoration: none;
            transition: 0.3s ease-in-out;

            &:hover,
            &.active{
              color:white;
            }
          }
        }
      }

    }
  
    .row-2{
      padding: 60px 0 100px 0;
      .social-icons{
        font-size: $fsize-footer-big;
        @include flex-cc;
        text-align: center;
        color: white;
  
        .social-i{
          margin: 0 10px;
          cursor:pointer;

          &:hover{
            color:$salvia-green;
          }
        }
      }
    }
  
  }

}

</style>
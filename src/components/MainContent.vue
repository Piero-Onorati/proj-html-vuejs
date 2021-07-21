<template>
  <main>

    <!-- start section-1: SHOP -->
    <section class="shop-section">

      <div class="container">

        <!--------------START SHOP BY CATEGORY -------------->
        <!-- first ROW -->
        <div class="row row-1">
          <div class="col-xs-12 heading">
            <h3>Browse by category</h3>
            <p>Augue purus et, tincidunt condimentum mauris. At nibh rutrum mi in. Nisi, vitae interdum eleifend dui, consequat nulla rhoncus dictum. Viverra.</p>
          </div>
        </div>

        <!-- second ROW -->
        <div class="row row-cards-1">
          <div class="col-xs-3 categories" v-for="(category,index) in categories" :key="index">
            <img :src="require('../assets/img/categories/'+category.name+'.jpg')" :alt="category.name">
            <h3>{{category.name}} ({{category.number}}) </h3>
          </div>
        </div>
        <!--------------END SHOP BY CATEGORY -------------->

        <!--------------START SHOP FOOD TYPE -------------->
        <div class="row row-3">
          <div class="col-xs-4" v-for="(type,index) in filteredFoodType" :key="index">
            <XlCard :element="type" />
          </div>
        </div>
        <!-------------- END SHOP FOOD TYPE --------------->

        <!------- START BANNER SHOP NEW ARRIVALS ---------->
        <div class="container">
          <div class="row">
            <Banner/>
          </div>
        </div>
        <!----------END BANNER SHOP NEW ARRIVALS ---------->

        <!--------------START SHOP BEST SELLER ------------>
        <div class="row row-5">
          <div class="col-xs-12 heading">
            <div class="txt">
              <span>All-time best sellers</span>
              <h3>Items everyone loves</h3>
            </div>
            <button>View all Products</button>

          </div>
        </div>
        <div class="row row-cards">
          <div class="col-xs-3" v-for="(product,index) in lovedProducts" :key="index"  >
            <Card :product="product"/>  
          </div>
          <div class="popups"></div>
        </div>
        <!-------------- END SHOP BEST SELLER ------------->

      </div>

    </section>
    <!-- end section-1 : SHOP -->

    <!-- start section-2: TESTIMONIALS -->
    <section class="testimonials">

      <!-------------- Section Title -------------->
      <div class="row">
        <div class="heading">
          <div class="overlay">
            <h2>Users testimonials</h2>
          </div>
        </div>
      </div>

      <!-------------- People Comments -------------->
      <div class="container fade-in">
        <div class="row">
          <div class="col-xs-4" v-for="(testimonial,index) in Testimonials" :key="index"  >
           <PersonCard :person="testimonial"/>
          </div>
        </div>
      </div>

    </section>
    <!-- end section-2: TESTIMONIALS -->

    <!-- start section-3: BANNER NEWSLETTER -->
    <div class="container">
      <div class="row">
        <BannerNewsL/>
      </div>
    </div>
    <!-- end section-3: BANNER NEWSLETTER -->

    <!-- start section-4: BLOG -->
    <section class="blog-section">

      <div class="container">

        <!-- firts ROW : TITLE -->
        <div class="row row-1">
          <div class="col-xs-12 heading">
            <h3>Get the best tips &amp; tricks</h3>
            <span>Recent articles</span>
          </div>
        </div>

        <!-- second ROW : ALL BLOG CARDS -->
        <div class="row row-cards"> 
          <div class="col-xs-3" v-for="(post,index) in blogArticle" :key="index"  >
            <BlogCard :article="post"/>
          </div>
        </div>

        <!-- third ROW : BUTTON -->
        <div class="row row-2">
          <div class="col-xs-12 button">
            <button>Read all the articles</button>
          </div>
        </div>
      </div>

    </section>
    <!-- end section-4: BLOG -->

    <!-- start section-5: HIGHLIGTHEDCONTENT -->
    <section class="highlithed">
      <div class="container-fuid">

        <div class="row row-1">
          <div class="col-xs-6 left">
            <div class="overlay">
              <div class="text">
                <span>find the best animals supplies</span>
                <h2>Popular accessories</h2>  
                <button>View all toys accessories</button>
              </div>
            </div>
          </div>
          <div class="col-xs-6 right">
            <div class="overlay">
              <div class="text">
                <span>find the best food</span>
                <h2>New food arrival</h2>  
                <button>View all food products</button>
              </div>
            </div>
          </div>
        </div>

        <!-- HIGHLIGTHEDCONTENT COMPONENT -->
        <div class="row row-2">
          <Highlighted/>  
        </div>
      </div>
      
    </section>
    <!-- end section-5: HIGHLIGTHEDCONTENT -->

    <!-- start section-6: LATEST-PRODUCT  -->
    <section class="latest-product">

      <div class="container">

        <!-- Title -->
        <div class="row row-1">
          <div class="col-xs-12 heading">
            <h3>New products arrivals</h3>
            <span>Latest products</span>
          </div>
        </div>

        <!-- All cards -->
        <div class="row row-cards">   
          <div class="col-xs-4" v-for="(product,index) in newProducts" :key="index"  >
            <Card :product="product"/>  
          </div>
        </div>
      </div>

    </section>
    <!-- end section-6: LATEST-PRODUCT  -->
    
  </main>
</template>

<script>

// Components.vue imported 
import Card from '@/components/Card.vue'
import XlCard from '@/components/XlCard.vue';
import BlogCard from '@/components/BlogCard';
import PersonCard from '@/components/PersonCard.vue';
import Banner from '@/components/Banner.vue';
import BannerNewsL from '@/components/BannerNewsL.vue';
import Highlighted from '@/components/Highlighted.vue';

// Data.js imported
import ProductList from '../data/ProductList.js';
import BlogPost from '../data/BlogPost.js';
import TestimonialsContent from '../data/TestimonialsContent.js';


export default {
  name:'MainContent',
  components:{
    Card,
    BlogCard,
    XlCard,
    Banner,
    BannerNewsL,
    PersonCard,
    Highlighted
  },
  data(){
    return{
      productList:ProductList,
      blogArticle:BlogPost,
      Testimonials:TestimonialsContent,
      lovedProducts:[],
      newProducts:[],
      categories:[],
      numberOfBed:0,
      numberOfFood:0,
      numberOfToys:0,
      numberOfTransport:0,
      foodType:[]
    }
  },

  computed:{
    filteredFoodType(){
      const seen = new Set();
      return this.foodType.filter(el => {
        const duplicate = seen.has(el.name);
        seen.add(el.name);
        return !duplicate;
      });
    }
  },

  created(){
    this.getlovedProducts();
    this.getNewProducts();
    this.getCategories();
    this.getnumberOf()
  },

  methods:{
    // Get all the loved product and put them into an array
    getlovedProducts(){
      this.productList.forEach(element => {
        if (element.loved == true) {
          this.lovedProducts.push(element)
        }
      });
    },

    // Get all the newest product and put them into an array
    getNewProducts(){
      this.productList.forEach(element => {
        if (element.new == true) {
          this.newProducts.push(element)
        }
      });
    },

    // Get the categories of the products
    getCategories(){
      this.productList.forEach(element =>{
        if(!this.categories.includes(element.category)){
          this.categories.push(element.category)
        } 
      });
      this.categories = this.categories.reduce(function(element, a){element.push({name: a});return element;}, []);
    },

    // Count the number of products for each categories
    // For "Food" category, create an array of object based on Food type
    getnumberOf(){
      this.productList.forEach(element => {
        if (element.category =='bed') {
          this.numberOfBed++;
          
        }else if(element.category =='food') {
          this.numberOfFood++;
          this.foodType.push(element.type);

        }else if(element.category =='toys') {
          this.numberOfToys++;
          
        }else if(element.category =='transport') {
          this.numberOfTransport++;
          
        } 
      });

      this.categories[0].number = this.numberOfBed;
      this.categories[1].number = this.numberOfFood;
      this.categories[2].number = this.numberOfToys;
      this.categories[3].number = this.numberOfTransport;
    }
  }

}
</script>

<style lang="scss" scoped>
@import '../style/mixins.scss';
@import '../style/vars.scss';


.shop-section{ 
  .row-1{
    padding-top:110px;

    .heading{
      text-align: center;
  
      h3{
        @include h3-heading
      }
  
      p{
        @include p-heading
      }
  
    }
  }

  .row-cards-1{
    padding: 70px 0;

    .categories{
      padding: 0 10px;
      text-align: center;

      img{
        width:100%
      }

      h3{
        padding-top: 10px;
        text-transform: capitalize;
        font-size:$card-didascalia;
        font-weight: 400;
      }
    }
  }

  .row-3{
    padding: 70px 0 110px 0;
  }
  .row-5{
    padding:110px 15px 0 15px;

    .heading{
      @include flex-between;
  
      span{
        @include span-heading;
      }
       h3{
        @include h3-heading;
      }
  
      button{
        @include green-button
      }
    }
  }
  .row-cards{
    padding: 50px 0;
  }

}

.testimonials{
  background-color: $dark-green;
  min-height: 700px;

  .heading{
    width: 100%;
    @include flex-cc;
    @include green-paw;

    .overlay{
      @include flex-cc;
      background-image: linear-gradient(#26422900,$dark-green);
      width: 100%;
      height: 100%;
      padding:80px 0 68px 0;

      h2{
        @include h2-heading
      }
    }
  }

}

.blog-section{
  
  .row-1{
    padding-top:100px;

    .heading{
      text-align: center;

      h3{
        @include h3-heading;
      }

      span{
        @include span-heading;
      }
    }
  }
  .row-cards{
    padding: 50px 0;
  }

  .row-2{
    .button{
      text-align: center;

      button{
        @include green-button
      }
    }
  }

}

.highlithed{
  .row-1{
    padding-top:100px;

    .left{
      width:100%;
      height:450px;
      background-image: url('../assets/img/banners/banner-3.jpg');
      background-size:cover ;
      background-position: center;
      cursor: pointer;
      transition: transform 0.3s ease-in-out;

      &:hover{
        transform: scale(1.03)
      }

      .overlay{
        @include flex-cc;
        width: 100%;
        height: 100%;
        background-color: rgba(0,0,0,0.2);

        .text{
          text-align: center;

          span{
            @include span-banner
          }
          h2{
            @include h2-heading;
            padding: 30px;
          }
          button{
            @include white-button-no-hover
          }
        }
      }
    }
    .right{
      width:100%;
      height:450px;
      background-image: url('../assets/img/banners/banner-4.jpg');
      background-size:cover ;
      background-position: center;
      cursor: pointer;
      transition: transform 0.3s ease-in-out;
      &:hover{
        transform: scale(1.03)
      }
      .overlay{
        @include flex-cc;
        width: 100%;
        height: 100%;
        background-color: rgba(0,0,0,0.2);
        .text{
          text-align: center;
          span{
            @include span-banner
          }
          h2{
            @include h2-heading;
            padding: 30px;
          }
          button{
            @include white-button-no-hover
          }
        }
      }
    }
  }
  .row-2{
    @include green-paw;
    height: 300px;
  }
}

.latest-product{
   .row-1{
    padding-top:100px;

    .heading{
      text-align: center;

      h3{
        @include h3-heading;
      }
      span{
        @include span-heading;
      }
    }
  }
  .row-cards{
    padding: 50px 0;
  }

}

</style>
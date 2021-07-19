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

        <!--------------START SHOP NEW ARRIVALS ------------>
        <div class="row row-4">
          <!-- BANNER COMPONENT -->
          <Banner/>
        </div>
        <!--------------END SHOP NEW ARRIVALS -------------->

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
        </div>
        <!-------------- END SHOP BEST SELLER ------------->

      </div>

    </section>
    <!-- end section-1 : SHOP -->

    <!-- start section-2: TESTIMONIALS -->
    <section>

      <div class="container">

        <!--------------START PEOPLE COMMENTS -------------->
        <div class="row">
          <div class="col-xs-4" v-for="(testimonial,index) in Testimonials" :key="index"  >
           <PersonCard :person="testimonial"/>
          </div>
         
          
        </div>
        <!-------------- END PEOPLE COMMENTS --------------->

        <!---------------- START NEWSLETTER ---------------->
        <div class="row">
          <!-- NEWSLETTER -->
          <!-- BANNER COMPONENT -->
          <Banner/>
        </div>
        <!------------------ END NEWSLETTER ---------------->

      </div>

    </section>
    <!-- end section-2: TESTIMONIALS -->

    <!-- start section-3: BLOG -->
    <section class="blog-section">

      <div class="container">

        <!-- firts ROW -->
        <div class="row row-1">
          <div class="col-xs-12 heading">
            <h3>Get the best tips &amp; tricks</h3>
            <span>Recent articles</span>
          </div>
        </div>

        <!-- second ROW -->
        <div class="row row-cards"> 
          <div class="col-xs-3" v-for="(post,index) in blogArticle" :key="index"  >
            <BlogCard :article="post"/>
          </div>
        </div>

        <!-- third ROW -->
        <div class="row">
          <button></button>
        </div>
      </div>

    </section>
    <!-- end section-3: BLOG -->

    <!-- start section-4: HIGHLIGTHEDCONTENT -->
    <section>
      <!-- HIGHLIGTHEDCONTENT COMPONENT -->
      <Highlighted/>
    </section>
    <!-- end section-4: HIGHLIGTHEDCONTENT -->

    <!-- start section-5: LATEST-PRODUCT  -->
    <section class="latest-product">

      <div class="container">

        <div class="row row-1">
          <div class="col-xs-12 heading">
            <h3>New products arrivals</h3>
            <span>Latest products</span>
          </div>
        </div>

        <div class="row row-cards">   
          <div class="col-xs-4" v-for="(product,index) in newProducts" :key="index"  >
            <Card :product="product"/>  
          </div>
        </div>
      </div>

    </section>
    <!-- end section-5: LATEST-PRODUCT  -->
    
  </main>
</template>

<script>

// Components.vue imported 
import Card from '@/components/Card.vue'
import XlCard from '@/components/XlCard.vue';
import BlogCard from '@/components/BlogCard';
import PersonCard from '@/components/PersonCard.vue';
import Banner from '@/components/Banner.vue';
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

.categories{
  padding: 0 10px;
  img{
    width:100%
  }
}

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
  }
  .row-5{
    padding-top:110px;
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

.blog-section{
  .row-1{
    padding-top:110px;
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

.latest-product{
   .row-1{
    padding-top:110px;
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
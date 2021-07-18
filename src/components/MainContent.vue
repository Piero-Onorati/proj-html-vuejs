<template>
  <main>

    <!-- start section-1: SHOP -->
    <section>

      <div class="container">

        <!--------------START SHOP BY CATEGORY -------------->
        <!-- first ROW -->
        <div class="row">
          <div class="col-xs-12">
            <h3></h3>
            <p></p>
          </div>
        </div>

        <!-- second ROW -->
        <div class="row">
          <div class="col-xs-3 categories" v-for="(category,index) in categories" :key="index">
            <img :src="require('../assets/img/categories/'+category.name+'.jpg')" :alt="category.name">
            <h3>{{category.name}} ({{category.number}}) </h3>
          </div>
        </div>
        <!--------------END SHOP BY CATEGORY -------------->

        <!--------------START SHOP FOOD TYPE -------------->
        <div class="row">
          <div class="col-xs-4">
            <div class="prova"></div>
            <!-- SHOP FOOD TYPE -->
            <!-- XL-CARD Component * 3 -->
            <!-- <XlCard/> -->
          </div>
          <div class="col-xs-4">
            <div class="prova"></div>
            <!-- SHOP FOOD TYPE -->
            <!-- XL-CARD Component * 3 -->
            <!-- <XlCard/> -->
          </div>
          <div class="col-xs-4">
            <div class="prova"></div>
            <!-- SHOP FOOD TYPE -->
            <!-- XL-CARD Component * 3 -->
            <!-- <XlCard/> -->
          </div>

        </div>
        <!-------------- END SHOP FOOD TYPE --------------->

        <!--------------START SHOP NEW ARRIVALS ------------>
        <div class="row">
          <!-- BANNER COMPONENT -->
          <Banner/>
        </div>
        <!--------------END SHOP NEW ARRIVALS -------------->

        <!--------------START SHOP BEST SELLER ------------>
        <div class="row">
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
          <!-- PEOPLE COMMENTS -->
          <!-- PERSON CARD COMPONENT * 3 -->
          <PersonCard/>
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
    <section>

      <div class="container">

        <!-- firts ROW -->
        <div class="row">
          <h3></h3>
          <p></p>
        </div>

        <!-- second ROW -->
        <div class="row">   
          <div class="col-xs-3 blog-post" v-for="(post,index) in blogArticle" :key="index"  >
            <img :src="require('../assets/img/blog/'+post.image+'.jpg')" :alt="post.name">
            <h3>{{post.title}}</h3>
            <h4>{{post.date}}</h4>
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
      <!-- HIGHLIGTHEDCONTENT COMPONENT -->
      <Highlighted/>
    <!-- end section-4: HIGHLIGTHEDCONTENT -->

    <!-- start section-5: LATEST-PRODUCT  -->
    <section>

      <div class="container">

        <div class="row">   
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
import Card from '@/components/Card.vue'
// import XlCard from '@/components/XlCard.vue';
import Banner from '@/components/Banner.vue';
import PersonCard from '@/components/PersonCard.vue';
import Highlighted from '@/components/Highlighted.vue';

import ProductList from '../data/ProductList.js';
import BlogPost from '../data/BlogPost.js';


export default {
    name:'MainContent',
    components:{
      Card,
      // MdCard,
      // XlCard,
      Banner,
      PersonCard,
      Highlighted
    },
    data(){
      return{
        productList:ProductList,
        lovedProducts:[],
        newProducts:[],
        categories:[],
        numberOfBed:0,
        numberOfFood:0,
        numberOfToys:0,
        numberOfTransport:0,
        blogArticle:BlogPost
      }
    },
    created(){
      this.getlovedProducts();
      this.getNewProducts();
      this.getCategories();
      this.getnumberOf()
    },
    methods:{

      getlovedProducts(){
        this.productList.forEach(element => {
          if (element.loved == true) {
            this.lovedProducts.push(element)
          }
        });
      },

      getNewProducts(){
        this.productList.forEach(element => {
          if (element.new == true) {
            this.newProducts.push(element)
          }
        });
      },

      getCategories(){
        this.productList.forEach(element =>{
          if(!this.categories.includes(element.category)){
            this.categories.push(element.category)
          } 
        });
        console.log(this.categories);
        this.categories = this.categories.reduce(function(element, a){element.push({name: a});return element;}, []);
        console.log(this.categories);
       
      },
    
      
      getnumberOf(){
        this.productList.forEach(element => {
          if (element.category =='bed') {
            this.numberOfBed++;
            
          }else if(element.category =='food') {
            this.numberOfFood++;
           
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
       

        console.log(this.categories);

      }
    }


}
</script>

<style lang="scss" scoped>
.categories{
  padding: 0 10px;
  img{
    width:100%
  }
}

.blog-post{
  padding: 0 10px;
  img{
    width:100%
  }
}

</style>
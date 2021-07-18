<template>
  <main>

    <!-- start section-1: SHOP -->
    <section>

      <div class="container">

        <div class="row">
          <!-- SHOP BY CATEGORY -->
          <div class="col-xs-12">
            <h3></h3>
            <p></p>
          </div>
          
        </div>

        <div class="row">
          <div class="col-xs-3" v-for="(product,index) in lovedProducts" :key="index"  >
            <Card :product="product"/>  
          </div>
        </div>

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

        <div class="row">
          <!-- BANNER COMPONENT -->
          <Banner/>
        </div>

        <div class="row">
          <!-- SHOP BEST SELLER -->
          <div class="col-xs-12">
            <div class="prova"></div>
            <h3></h3>
            <p></p>
          </div>
          
        </div>

        <div class="row">
          <div class="col-xs-3">
            <div class="prova"></div>
            <!-- XS-CARD Component * 4 -->
         
          </div>
          <div class="col-xs-3">
            <div class="prova"></div>
            <!-- XS-CARD Component * 4 -->
           
          </div>
          <div class="col-xs-3">
            <div class="prova"></div>
            <!-- XS-CARD Component * 4 -->
          
          </div>
          <div class="col-xs-3">
            <div class="prova"></div>
            <!-- XS-CARD Component * 4 -->
            
          </div>
        </div>

      </div>


    </section>
    <!-- end section-1 : SHOP -->

    <!-- start section-2: TESTIMONIALS -->
    <section>

      <!-- PEOPLE COMMENTS -->
      <!-- PERSON CARD COMPONENT * 3 -->
      <PersonCard/>

      <!-- NEWSLETTER -->
      <!-- BANNER COMPONENT -->
      <Banner/>

    </section>
    <!-- end section-2: TESTIMONIALS -->

    <!-- start section-3: BLOG -->
    <section>

      <h3></h3>
      <p></p>
      <!-- XS-CARD COMPONENT * 4 -->
      <!-- <XsCard/> -->

      <button></button>

      <!-- HIGHLIGTHEDCONTENT COMPONENT -->
      <Highlighted/>

    </section>
    <!-- end section-3: BLOG -->

    <!-- start section-4: LATEST-PRODUCT  -->
    <section>
      <div class="container">
        <div class="row">   
          <div class="col-xs-4" v-for="(product,index) in newProducts" :key="index"  >
            <Card :product="product"/>  
          </div>
        </div>
      </div>
    </section>
    <!-- end section-4: LATEST-PRODUCT  -->
    
  </main>
</template>

<script>
import Card from '@/components/Card.vue'
// import MdCard from '@/components/MdCard.vue';
// import XlCard from '@/components/XlCard.vue';
import Banner from '@/components/Banner.vue';
import PersonCard from '@/components/PersonCard.vue';
import Highlighted from '@/components/Highlighted.vue';

import ProductList from '../data/ProductList.js';


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
        newProducts:[]
      }
    },
    created(){
      this.getlovedProducts();
      this.getNewProducts()
    },
    methods:{
      getlovedProducts(){
        this.productList.forEach(element => {
          if (element.loved == true) {
            this.lovedProducts.push(element)
          }

          console.log(this.newProducts);
        });
      },
      getNewProducts(){
        this.productList.forEach(element => {
          if (element.new == true) {
            this.newProducts.push(element)
          }

          console.log(this.newProducts);
        });
      },
    }


}
</script>

<style lang="scss" scoped>
.green{
  background-color: chartreuse;
}
.prova{
  background-color: burlywood;
  border:1px solid chocolate;
  height: 200px;
}

</style>
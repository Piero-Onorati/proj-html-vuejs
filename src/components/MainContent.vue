<template>
  <main>

    <!-- start section-1: SHOP -->
    <section>

      <!-- SHOP BY CATEGORY -->
      <h3></h3>
      <p></p>
      <!-- XS-CARD Component * 4 -->
      <XsCard/>

      <!-- SHOP FOOD TYPE -->
      <!-- XL-CARD Component * 3 -->
      <XlCard/>

      <!-- BANNER COMPONENT -->
      <Banner/>

      <!-- SHOP BEST SELLER -->
      <h3></h3>
      <p></p>
      <!-- XS-CARD Component * 4 -->
      <XsCard/>

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
      <XsCard/>

      <button></button>

      <!-- HIGHLIGTHEDCONTENT COMPONENT -->
      <Highlighted/>

    </section>
    <!-- end section-3: BLOG -->

    <!-- start section-4: LATEST-PRODUCT  -->
    <section>
      <!-- MD-CARD COMPONENT * 6 -->
      <MdCard/>
    </section>
    <!-- end section-4: LATEST-PRODUCT  -->
    
  </main>
</template>

<script>
import XsCard from '@/components/XsCard.vue';
import MdCard from '@/components/MdCard.vue';
import XlCard from '@/components/XlCard.vue';
import Banner from '@/components/Banner.vue';
import PersonCard from '@/components/PersonCard.vue';
import Highlighted from '@/components/Highlighted.vue'


export default {
    name:'MainContent',
    components:{
      XsCard,
      MdCard,
      XlCard,
      Banner,
      PersonCard,
      Highlighted
    }


}
</script>

<style>

</style>
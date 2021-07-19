<template>
    <div class="card">
        <img :src="require('../assets/img/foodtype/'+element.img+'.png')" :alt="element.name">
        <h3>{{element.name}}</h3>
        <span>{{element.description}}</span>
        
    </div>
  
</template>

<script>
export default {
    name:'XlCard',
    props:{
        element:Object
    }

}
</script>

<style>

</style>
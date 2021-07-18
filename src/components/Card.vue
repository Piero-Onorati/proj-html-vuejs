<template>
<div class="card">
    <img :src="require('../assets/img/'+product.image+'.jpg')" alt="">
    {{product.name}}
</div>
  
</template>

<script>
export default {
    name:'Card',
    props:{
        product:Object
    }

}
</script>

<style lang="scss" scoped>

.card{
    width:100%;
    img{
        width: 100%;
    }
}

</style>
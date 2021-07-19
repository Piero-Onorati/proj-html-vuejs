<template>
<div class="card">
    <img :src="require('../assets/img/avatars/'+person.photo+'.jpg')" :alt="person.name">
    <p>{{person.says}}</p>
    <span>{{person.name}}, {{person.from}}</span>

</div>
  
</template>

<script>
export default {
    name:'PersonCard',
    props:{
        person:Object
    }

}
</script>

<style lang="scss" scoped>

</style>
<template>
  <div class="card">
    <img :src="require('../assets/img/blog/'+ article.image +'.jpg')" :alt="article.name">
    <div class="card-description">
        <h3>{{article.title}}</h3>
        <h4>{{article.date}}</h4>
    </div>
  </div>
</template>

<script>
export default {
    name:'BlogPost',
    props:{
        article:Object
    }
}
</script>

<style lang="scss" scoped>

.card{
  padding: 0 10px;

  img{
    width:100%
  }

  .card-description{
      width: 100%;
  }
}

</style>
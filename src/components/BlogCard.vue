<template>
  <div class="card">

    <!-- CARD IMAGE: img + card-info -->
    <div class="card-image">
      <img :src="require('../assets/img/blog/'+ article.image +'.jpg')" :alt="article.name">

      <!-- Card info (appears on hover) -->
      <div class="card-info">
        <h3>{{article.title}}</h3>
        <span>Tips and Tricks</span>
      </div>

    </div>
    
    <!-- CARD DESCRIPTION -->
    <div class="card-description">
      <h3>{{article.title}}</h3>
      <h4>{{article.date}}</h4>
    </div>

  </div>
</template>

<script>
export default {
    name:'BlogCard',
    props:{
      article:Object
    }
}
</script>

<style lang="scss" scoped>
@import '../style/mixins.scss';
@import '../style/vars.scss';

.card{
  padding: 0 15px;

    .card-image{
      width: 100%;
      position: relative;

      &:hover .card-info{
        opacity:1;  
      }
  
      img{
        width:100%;
        height: 100%;       
      }

      .card-info{
        @include flex-cc;
        flex-direction: column;
        background:linear-gradient( $sepia-skin 99%, transparent 1% );
        color: white;
        text-align: center;
        padding: 20px;
        opacity:0;
        width:100%;
        height: 100%;
        position: absolute;
        top:50%;
        left:50%;
        transform: translate(-50%,-50%);
        transition: all 0.5s ease-in-out;

        h3{
          font-weight:400;
          font-size: $card-didascalia;
          line-height: 35px;
        }

        span{
          padding-top:10px ;
          font-size: 15px;
          font-weight: 300;
        }
      }
    }

  .card-description{
    @include flex-cc;
    width: 100%;
    padding:30px 25px;
    flex-direction:column;

    h3{
      font-size:24px;
      font-weight: 400;
      line-height: 38px;
    }

    h4{
      align-self: flex-start;
      font-weight: 300;
      padding-top:8px ;
    }
  }
}

</style>
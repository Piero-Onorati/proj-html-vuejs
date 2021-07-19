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
@import '../style/mixins.scss';
@import '../style/vars.scss';

.card{
    @include flex-cc;
    flex-direction: column;
    padding-bottom: 70px;
    img{
        border-radius:50%;
        width:100px
    }
    p{
        color: white;
        text-align: center;
        font-size:$fsize-heading-paragh;
        line-height: 38px;
        padding:25px 50px 30px 50px;
    }

    span{
        color:$salvia-green;
        font-size:$fsize-heading-span;
    }
    
}

</style>
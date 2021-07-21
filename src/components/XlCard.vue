<template>
    <div class="card">

        <!-- Title + description -->
        <div class="heading">      
            <h3>{{element.name}}</h3>
            <span>{{element.description}}</span>
        </div>

        <!-- IMG -->
        <img :src="require('../assets/img/foodtype/'+element.img+'.png')" :alt="element.name">
        <!-- Butoon -->
        <button>Shop {{element.name}} food</button>
        
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

<style lang="scss" scoped>
@import '../style/mixins.scss';
@import '../style/vars.scss';

.card{
    background-color: $dark-green;
    margin: 0 10px;
    @include flex-cc;
    flex-direction:column;
    padding-bottom: 75px;
    filter:brightness(0.9);
    transition: transform 0.3s ease-in-out;
    cursor:pointer;

    &:hover{
        transform: scale(1.05);
        filter:brightness(1);
    }

    .heading{
        @include flex-cc;
        flex-direction:column;
        width: 100%;
        padding:80px 0 68px 0;
        background-image: url('../assets/img/bg-transparent-3.png');

        h3{
            font-family: "Trocchi";
            font-size: 35px;
            font-weight:300;
            color: white;
        }
        span{
            padding-top: 15px;
            font-size: 22px;
            font-weight: 500;
            color:#60ba6e
        }
    }

    img{
        width: 60%
    }

    button{
        background-color: $green;
        color: white;
        font-size: 15px;
        font-weight: $fweight-medium;
        font-family: 'Work Sans';
        border-radius: 30px;
        border:none;
        padding:14px 30px;
        margin-top: 20px;
    }
}

</style>
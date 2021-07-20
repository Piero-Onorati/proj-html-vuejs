<template>
<div class="card">
    <div class="overlay">
        <img :src="require('../assets/img/'+product.image+'.jpg')" alt="">
        <div class="card-info">
            <div class="stars">
                <span v-for="(start,index) in Math.ceil(product.vote/2)" :key="index" >
                    <i class="fas fa-star"></i>
                </span>
                <span v-for="(start,index) in 5 - Math.ceil(product.vote/2)" :key="'a'+ index" >
                    <i class="far fa-star"></i>
                </span>
            </div>
            <div class="buttons">
                <button>Add to cart</button> 
                <span>&#8725;</span>  
                <button>Quick view</button>
            </div>
        </div>
    </div>
    <div class="card-description" :class="(product.loved == true) ? 'card-description-1' : 'card-description-2'">
        <h3>{{product.name}}</h3>
        <span :class="(product.sale == 'yes')? 'discounted':''">&dollar; {{product.price.toFixed(2)}}</span>
        <span v-if="product.sale == 'yes'">&dollar; {{product.discountedPrice.toFixed(2)}}</span>
    </div>
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
@import '../style/mixins.scss';
@import '../style/vars.scss';

.card{
    width:100%;
    padding: 0 15px;
    .overlay{
        position: relative;
        width:100%;

        &:hover .card-info{
            opacity:1;
        }
       
        img{
            width: 100%;
        }

        .card-info{
            @include flex-cc;
            flex-direction: column;
            width: 100%;
            height: 100%;
            position: absolute;
            background:linear-gradient( $sepia-skin 99%, transparent 1% );
            top:50%;
            left:50%;
            transform: translate(-50%,-50%);
            opacity:0;
            transition: all 0.5s ease-in-out;

            .stars{
                color: white;
                padding-bottom:20px;
            }

            .buttons{

                button{
                    background: transparent;
                    border: none;
                    color: white;
                    text-transform: uppercase;
                    font-weight: 300;
                    font-size: $fsize-heading-xs;
                    padding: 0 20px;
                    cursor: pointer;
                }

                span{
                    color:white;
                }

            }
        }
    }

    .card-description-1{
        
        h3{
          padding:20px 0 10px 0;
          font-weight:400;
          font-size: $card-didascalia;
          line-height: 35px;
        }

        span{
            color: $green;
            font-weight:400;
            font-size:$card-price-didascalia;
        }

        .discounted{
            text-decoration: line-through;
            font-size:16px;
            padding-right:10px
        }
    }


    .card-description-2{
        text-align: center;
        padding-bottom: 50px;
        h3{
          padding:20px 0 10px 0;
          font-weight:400;
          font-size: $card-didascalia;
          line-height: 35px;
          font-style: italic;
        }

        span{
            color: $green;
            font-weight:400;
            font-size:20px;
        }

        .discounted{
            text-decoration: line-through;
            font-size:16px;
            padding-right:10px
        }
    }
    
    
}

</style>
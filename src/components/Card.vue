<template>
<div class="card">

    <!-- CARD IMAGE BOX (contain IMG + SALE TAG + CARD-INFO on hover) -->
    <div class="overlay">

        <img :src="require('../assets/img/'+product.image+'.jpg')" :alt="product.name">

        <!-- SALE tag -->
        <div class="sale" v-if="product.sale == 'yes'">
            <span>Sale!</span>
        </div>

        <!-- CARD INFO that appears on hover (contains: rate star system + buttons for 'add to cart' and 'quick view') -->
        <div class="card-info">

            <!-- Star rate system -->
            <div class="stars">
                <span v-for="(start,index) in Math.ceil(product.vote/2)" :key="index" >
                    <i class="fas fa-star"></i>
                </span>
                <span v-for="(start,index) in 5 - Math.ceil(product.vote/2)" :key="'a'+ index" >
                    <i class="far fa-star"></i>
                </span>
            </div>

            <!-- Add to cart / Quick view -->
            <div class="buttons">
                <button>Add to cart</button> 
                <span>&#8725;</span>  
                <button @click="showModal = true">Quick view</button>
                
            </div>
           
        </div>

    </div>

    <!-- CARD DESCRIPTION (contains: product name + price) -->
    <div class="card-description" :class="(product.loved == true) ? 'card-description-1' : 'card-description-2'">

        <!-- Product name -->
        <h3>{{product.name}}</h3>

        <!-- Price -->
        <span :class="(product.sale == 'yes')? 'discounted':''">&dollar; {{product.price.toFixed(2)}}</span>
        <span v-if="product.sale == 'yes'">&dollar; {{product.discountedPrice.toFixed(2)}}</span>

    </div>

    <!-- CARD MODAL that appears when click 'Quick view' -->
    <transition name="fade">
        <div class="card-modal" v-if="showModal">

            <!-- IMAGE (on the left) -->
            <div class="img-modal">
                <img :src="require('../assets/img/'+product.image+'.jpg')" :alt="product.name">
            </div>

            <!-- BODY (on the right) -->
            <div class="body-modal">

                <div class="body-modal-box">

                    <!-- Heading: TITLE + CLOSE BUTTON -->
                    <div class="heading-modal">
                        <h3>{{product.name}}</h3>
                        <button  @click="showModal=false"><i class="fas fa-times"></i></button>
                    </div>

                    <!-- DETAILS: PRICE + STARS -->
                    <div class="details">

                        <!-- PRICE -->
                        <div class="price">
                            <span :class="(product.sale == 'yes')? 'discounted':''">&dollar; {{product.price.toFixed(2)}}</span>
                            <span v-if="product.sale == 'yes'">&dollar; {{product.discountedPrice.toFixed(2)}}</span>
                        </div>

                        <!-- STARS RATE SYSTEM -->
                        <div class="stars">
                            <span v-for="(start,index) in Math.ceil(product.vote/2)" :key="index" >
                                <i class="fas fa-star"></i>
                                </span>
                            <span v-for="(start,index) in 5 - Math.ceil(product.vote/2)" :key="'a'+ index" >
                                <i class="far fa-star"></i>
                            </span>
                        </div>

                    </div>

                    <!-- PRODUCT DESCRIPTION -->
                    <p>{{product.description}}</p>

                    <!-- SHOPPING BUTTONS -->
                    <div class="shopping-buttons">

                        <!-- Div for icrease, decrease the number of items -->
                        <div class="add-item">
                            <button class="subtract" @click="subtract"><i class="fas fa-minus"></i></button>
                            <span>{{counter}}</span>
                            <button class="add" @click="add"><i class="fas fa-plus"></i></button>
                        </div>

                        <!-- Button -->
                        <button class="add-to-cart">Add to cart</button>
                    </div>

                </div>

                <div class="view">View Details</div>
            </div>

        </div>
    </transition>

    <!-- background that appears when card-modal is shown -->
    <div class="background" v-if="showModal"></div>

</div>
  
</template>

<script>
export default {
    name:'Card',
    props:{
        product:Object
    },
    data(){
        return{
            showModal: false,
            counter:1
        }
    },

    methods:{
        subtract(){
            if (this.counter<=0) {
                this.counter=0
            }else{
                this.counter--
            }
        },

        add(){
            this.counter++
        }
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

        .sale{
                @include flex-cc;
                width:50px;
                height: 50px;
                border-radius: 50%;
                color:white;
                background-color: $green;
                position: absolute;
                top:15px;
                left:15px;
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

    .card-modal{
        @include flex-cc;
        width:900px;
        height: 400px;
        display: flex;
        background-color: white;
        border-radius: 10px;
        overflow: hidden;
        position: fixed;
        top:50%;
        left: 50%;
        transform: translate(-50%,-50%);
        transition: all 0.3s ease-in-out;
        z-index: 12;

        .img-modal{
            width: 400px;
            img{
                width: 100%;
            }
        }

        .body-modal{
            width: calc(100% - 400px);
            height: 100%;

            .body-modal-box{
                padding: 0 20px;
                height: calc(100% - 50px);
                overflow-y: auto;

                .heading-modal{
                    @include flex-between;
                    padding:20px 0;

                    h3{
                        padding:20px 0 0 0;
                        font-weight:400;
                        font-size: $card-didascalia;
                        line-height: 35px;
                    }

                    button{
                        background-color: transparent;
                        border:none;
                        color:$grey;
                        font-size: $fsize-input-button;   
                    }
                }

                .details{
                    display: flex;
                    align-items: center;
                    width:80%;

                    .price{
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

                    .stars{
                        margin-left:30px;
                        color:$green;
                    }
                }

                p{
                    font-size: $fsize-heading-paragh;
                    line-height: 34px;
                    padding-top:45px
                }

                .shopping-buttons{
                    @include flex-between;
                    padding: 50px 0;
                    width: 80%;
                    
                    .add-item{
                        @include flex-cc;
                        width:150px;
                        border-radius: 30px;
                        border:1px solid $grey;
                        font-size: 15px;

                        .subtract{
                            @include flex-cc;
                            width:50px;
                            background-color: transparent;
                            border:none;
                            cursor: pointer;
                            color:$grey
                        }

                        span{
                            @include flex-cc;
                            padding:12px 0;
                            width:50px;
                            border-left: 1px solid $grey;
                            border-right: 1px solid $grey;
                        }

                        .add{
                            @include flex-cc;
                            width:50px;
                            background-color: transparent;
                            border:none;
                            cursor: pointer;
                            color:$grey
                        }

                    }

                    .add-to-cart{
                        @include green-button

                    }
                }

            }

            .view{
                @include flex-cc;
                width:100%;
                height:50px;
                background-color: $green;
                color: white;
                font-size: 16px;
                font-weight: $fweight-medium;
                font-family: 'Work Sans';
                cursor: pointer;

                &:hover {
                background-color: darken($green, 8%);
                }
                
            }
            
        }
        
    }

    .fade-enter-active, .fade-leave-active {
        transition: opacity .4s;
    }
    .fade-enter, .fade-leave-active {
        opacity: 0;
    }

    .background{
        position: fixed;
        top:0;
        left:0;
        bottom:0;
        right: 0;
        transition: 200ms ease-in-out;
        background-color: rgba(0,0,0, 0.5);
        pointer-events: none;
        z-index: 11;
    }

}

</style>
<template>

    <nav id="navbar">

        <div class="container">

            <div class="row">

                <!-- LOGO -->
                <div class="logo col-xs-2" id="logo" >
                    <img src="../assets/img/logo-symbol.png" alt="logo-pet-supply">
                </div>

                <div class="nav col-xs-8">

                    <!-- Links WITH DROPDOWN -->
                    <ul class="menu">
                        <li v-for="(link,index) in Links" :key="index" @mouseover="mouseOver(index)" @mouseleave="mouseOut(index)">
                    
                            <a :href="link.url" :class="{ active:link.active }">{{link.name}}</a>
                            <i class="fas fa-chevron-down arrow" v-if="link.dropdown !=''|| link.megaMenu !=''" :class="{ active:link.active }"></i>

                            <transition name="fade">
                                
                                <ul class="dropdown" v-if="dropdown && index == checkIndex" @click="dropdown = false">
                                    <li v-for="(drop,index) in link.dropdown" :key="index" ><a href="#">{{drop}}</a></li>
                                </ul>
                            
                            </transition>

                        </li>
                    </ul>

                    <div class="mega-menu">
                        
                        <div class="btn-mega"><span>Shop by brand</span> <i class="fas fa-chevron-down arrow"></i></div>
                        
                        <div class="mega-menu-content">
                            <div class="card-mega-menu-1">
                                <img src="../assets/img/mega-1.jpg" alt="">
                                <div class="heading-1">
                                    <h3>Frozen</h3>
                                    <span>Freeze-Dried dog food</span>
                                    
                                </div>
                            </div>
                            <div class="card-mega-menu-2">
                                <img src="../assets/img/mega-2.jpg" alt="">
                                <div class="heading-2">
                                    <h3>Kibble</h3>
                                    <span>Dry dog food</span>
                                </div>
                            </div>
                            <div class="card-mega-menu-3">
                                <img src="../assets/img/mega-3.jpg" alt="">
                                <div class="heading-3">
                                    <h3>Moist</h3>
                                    <span>Dry dog food</span>
                                </div>
                            </div>
                        
                        </div>
                    </div>

                </div>

                <!-- SHOPPING ICONS -->
                <div class="shopping col-xs-2" id="s-icons">
                    <i class="fas fa-shopping-bag shopping-icon"></i>
                    <i class="far fa-user shopping-icon"></i>
                </div>

            </div>


        </div>     
        
    </nav>

</template>

<script>
import NavLinks from '../data/NavLinks.js';

export default {
    name: 'Navbar',

    data(){
        return{
            Links:NavLinks,
            dropdown:false,
            checkIndex:''
        }
    },

    methods:{
        mouseOver: function(index){
            this.checkIndex = index;
            this.dropdown = true 
        },

        mouseOut(index){
            this.checkIndex = index;
            this.dropdown = false
        }

    }    


}
</script>

<style lang="scss" scoped>
@import '../style/mixins.scss';
@import '../style/vars.scss';


nav{
    background-color: white;
    position: sticky;
    top:0;
    z-index: 99999;
    width: 100%;
    transition: top 0.3s;
   
    
    .logo{
        @include flex-start-center;
        
        img{
            width:35px
        }
    }

    .nav{
        @include flex-cc;
        .menu{
            display: flex;

            li{
                display:flex;
                align-items: center;
                position: relative;
                list-style: none;
                &:hover .arrow{
                    color: black;
                }

                .arrow{
                    color: $grey;
                    &:hover,
                    &.active{
                        color: black;
                    }
                }

                a{
                    display: block;
                    padding: 25px 10px 25px 20px;
                    color: $grey;
                    text-decoration: none;
                    font-weight: 500;
                    transition: 0.3s ease;

                    &:hover,
                    &.active{
                        color: black;
                    }
                }

                .dropdown{
                    position:absolute;
                    top:100%;
                    left:-10px;
                    display: flex;
                    flex-direction:column;

                    li{
                        width:200px;
                        background: white;
                        transition: background .2s;
                        border: 1px solid lightgray;

                        &:hover{
                        background: $green;
                        }

                        a{
                            color: black;
                            font-weight: 400;
                            &:hover{
                                color:white
                            }
                        }
                    }
                    
                }

            }

        }

        .mega-menu{
            .btn-mega{
                padding:25px 20px;
                display: block;
                color: $grey;

                span{
                    padding-right: 5px;
                }

                &:hover {
                    color: black;
                }
            }

            .mega-menu-content {
                display: none;
                position: absolute;
                background-color: #f9f9f9;
                width: 100%;
                left: 0;
                z-index: 1;

                .card-mega-menu-1,
                .card-mega-menu-2,
                .card-mega-menu-3{
                    position:relative;
                    width: calc(100% / 3);
                    height: 250px;
                    img{
                        width: 100%;
                        height: 100%;
                    }

                    .heading-1,
                    .heading-2,
                    .heading-3{
                        text-align: left;
                        position: absolute;
                        bottom:30px;
                        left:50px;

                        h3{
                            font-family: "Trocchi";
                            font-size: 35px;
                            font-weight:300;
                            color: black;
                            padding-bottom: 20px;
                        }
                        span{
                            font-size: 18px;
                            font-weight: 500;
                            color:$dark-green
                        }
                    }
                }

                
                
            }

            &:hover .mega-menu-content {
                display: flex;
            }

        }

    }

    .shopping {
        @include flex-end-center;
        font-size: 24px;
        .shopping-icon{
            margin-left:15px
        }
    }

}

</style>
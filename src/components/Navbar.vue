<template>

    <nav>

        <div class="container">

            <div class="row">

                <!-- LOGO -->
                <div class="logo col-xs-2">
                    <img src="../assets/img/logo-symbol.png" alt="logo-pet-supply">
                </div>

                <div class="nav col-xs-8">

                    <!-- Links WITH DROPDOWN -->
                    <ul class="menu">
                        <li v-for="(link,index) in Links" :key="index" @mouseover="mouseOver(index)" @mouseleave="mouseOut(index)">
                    
                            <a :href="link.url">{{link.name}}</a>
                            <i class="fas fa-chevron-down" v-if="link.dropdown !=''|| link.megaMenu !=''"></i>

                            <transition name="fade">
                                
                                <ul class="dropdown" v-if="dropdown && index == checkIndex" @click="dropdown = false">
                                    <li v-for="(drop,index) in link.dropdown" :key="index" ><a href="#">{{drop}}</a></li>
                                </ul>
                            
                            </transition>

                        </li>
                    </ul>

                    <div class="mega-menu">
                        
                        <span>Shop by brand<i class="fas fa-chevron-down"></i></span>
                        
                        <div class="mega-menu-content">
                            <div class="card-mega-menu">
                                <img src="../assets/img/mega-1.jpg" alt="">

                            </div>
                            <div class="card-mega-menu">
                                <img src="../assets/img/mega-2.jpg" alt="">

                            </div>
                            <div class="card-mega-menu">
                                <img src="../assets/img/mega-3.jpg" alt="">

                            </div>
                        
                        </div>
                    </div>

                </div>

                <!-- SHOPPING ICONS -->
                <div class="shopping col-xs-2">
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


nav{
    background-color: white;
    
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
    
                         
    
                    a{
                       
                        display: block;
                        padding: 25px 10px 25px 20px;
                        color: black;
                        text-decoration: none;
                    }
    
                    .dropdown{
                        position:absolute;
                        top:100%;
                        left:-10px;
                        display: flex;
                        flex-direction:column;
    
                        li{
                            width:200px;
                            background: #333;
                            transition: background .2s;
    
                            &:hover{
                            background: #444;
                            }
                        }
                        
                        
                        
                    }
    
                }
    
            }
    
            .mega-menu{

                span{
                    padding:25px 20px;
                    display: block;
                }
    
                .mega-menu-content {
                    display: none;
                    position: absolute;
                    background-color: #f9f9f9;
                    width: 100%;
                    left: 0;
                    z-index: 1;
    
                    .card-mega-menu{
                        width: calc(100% / 3);
                        height: 250px;
                        img{
                            width: 100%;
                            height: 100%;
                       
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
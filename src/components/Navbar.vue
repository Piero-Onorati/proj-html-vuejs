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

                        <transition name="fade">
                        
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

                        </transition>
                    </div>

                </div>

                <!-- SHOPPING ICONS -->
                <div class="col-xs-2" id="shopping">
                    <i class="fas fa-shopping-bag shopping-icon"></i>
                    <div class="user-icon">
                        <i class="far fa-user"></i>
                        <div class="subscribe">
                        <div class="input-box">
                            <input type="text" placeholder="Username">
                        </div>
                        <div class="input-box">
                            <input type="password" placeholder="Password">
                        </div>

                        <div class="check-box">
                            <input type="checkbox" id="accept-terms">
                            <label for="accept-terms" class="checkbox-label">Remember Me</label>
                        </div>

                        <div class="buttons">
                            <button class="log-in">Log In</button>
                            <button class="register">Register</button>
                        </div>

                        </div>
                    </div>
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
    created(){
       this.showHidden()


    },

    methods:{
        mouseOver: function(index){
            this.checkIndex = index;
            this.dropdown = true 
        },

        mouseOut(index){
            this.checkIndex = index;
            this.dropdown = false
        },

        showHidden(){
            window.onscroll = function() {scrollFunction()};

            function scrollFunction() {
            if (document.body.scrollTop > 80 || document.documentElement.scrollTop > 80) {
                document.getElementById("logo").style.visibility = "visible";
                document.getElementById("shopping").style.visibility = "visible";
            } else {
                document.getElementById("logo").style.visibility = "hidden";
                document.getElementById("shopping").style.visibility = "hidden";
            }
            }
        }


    }    


}
</script>

<style lang="scss" scoped>
@import '../style/mixins.scss';
@import '../style/vars.scss';


nav{
    background-color: white;
    border-bottom: 1px solid $dark-green;
    position: sticky;
    top:0;
    z-index: 9;
    width: 100%;
    transition: top 0.3s;
   
    
    #logo{
        @include flex-start-center;
        visibility: hidden;
        
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
                        border-bottom: 1px solid lightgray;

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
                .fade-enter-active, .fade-leave-active {
                    transition: opacity .2s;
                }
                .fade-enter, .fade-leave-active {
                    opacity: 0;
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

    #shopping {
        @include flex-end-center;
        font-size: 22px;
        visibility: hidden;

      .shopping-icon{
        &:hover{
          color:$green;
        }
      }
  
      .user-icon{
        margin-left:20px;
        position: relative;

        &:hover{
          color:$green;
        }

        .subscribe{
          position: absolute;
          right:0;
          top:100%;
          background-color: white;
          padding: 20px;
          z-index:10;
          display: none;

          .input-box{
            background-color: $sand;
            border-radius: 30px;
            width:100%;
            margin:10px auto;
            padding: 16px 10px;
            input{
              background-color: transparent;
              border:none;
              padding-left: 8px;
              font-size: $fsize-input-placeholder;

              &::placeholder{
                font-size: $fsize-input-placeholder;
                font-family: 'Work Sans';
              }
            }
          }

          .check-box{
            @include flex-start-center;
            margin-top:20px;
            .checkbox-label{
              font-size:14px;
              padding-left: 5px;
            }
          }
          .buttons{
            width:100%;
            display: flex;
            flex-direction: column;
            align-items: flex-end;

            .log-in{
              background-color: $green;
              color: white;
              font-size: 15px;
              font-weight: $fweight-medium;
              font-family: 'Work Sans';
              border-radius: 30px;
              border:none;
              padding:10px 22px;
              margin:10px 0;
              cursor: pointer;
    
              &:hover {
              background-color: darken($green, 8%);
              }
            }
            .register{
              background-color:white; 
              color: $green;
              width:90px;
              font-size: 14px;
              font-weight: $fweight-medium;
              font-family: 'Work Sans';
              border-radius: 30px;
              border:none;
              padding:10px 20px;
              cursor: pointer;;
            }

          }
        }

        &:hover .subscribe{
          display: block ;
        }
      }
    }

}

</style>
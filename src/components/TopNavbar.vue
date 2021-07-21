<template>

  <nav id="navbar">

    <div class="container">

      <div class="row">

        <!-- LOGO -->
        <div class="logo col-xs-3">
          <img src="../assets/img/dark-pet-logo.png" alt="logo">
        </div>

        <!-- SEARCH-BOX-->
        <div class="col-xs-3 search-box-container">
          <div class="search-box">
            <label for="serch-box-nav"><i class="fas fa-search"></i></label>
            <input type="text" id="serch-box-nav" placeholder="Search...">
          </div>
        </div>

        <!-- QUESTIONS -->
        <div class="question col-xs-5">
          <span><strong>Questions?</strong>  Call us : 1.800.123.4567</span>
        </div>

        <!-- SHOPPING ICONS -->
        <div class="shopping col-xs-1">
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
export default {
  name:'TopNavbar',
}
</script>

<style lang="scss" scoped>
@import '../style/mixins.scss';
@import '../style/vars.scss';

nav{
  background-color: white;
  border-bottom: 1px solid lightgray;

 

  .row{
    padding: 15px 0;
    
    .logo{
      @include flex-start-center;

      img{
        width: 240px;
      }
    }
  
    .search-box-container{ 
      @include flex-cc;

      .search-box{
        @include flex-start-center;
        background-color: #f2f4f3;
        width: 350px;
        border-radius: 30px;
        padding: 14px ;
  
        input{
          background-color: transparent;
          outline: none;
          border:none;
          margin-left: 20px;
        }
  
      }
    }

    .question{
      @include flex-cc;
    }
  
    .shopping {
      @include flex-end-center;
      font-size: 22px;

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

}

</style>
<template>

  <nav>

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
        <div class="question col-xs-4">
          <span><strong>Questions?</strong>  Call us : 1.800.123.4567</span>
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
export default {
    name:'TopNavbar'

}
</script>

<style lang="scss" scoped>
@import '../style/mixins.scss';

nav{
  background-color: white;
  border-bottom: 1px solid grey;

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
        padding: 14px 10px;
  
        input{
          background-color: transparent;
          outline: none;
          border:none;
  
          &::placeholder{
            padding-left:20px;
          }
        }
  
      }
    }
    .question{
      @include flex-cc;
    }
  
    .shopping {
      @include flex-end-center;
      font-size: 24px;
  
      .shopping-icon{
        margin-left:15px
      }
    }

  }

}

</style>
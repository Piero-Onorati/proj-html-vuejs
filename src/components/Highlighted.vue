<template>
<div class="overlay">
    <div class="container">
        <div class="row">

            <!-- First Item -->
            <div class="item">
                <i class="fas fa-truck icon"></i>
                <h3>Free worldwide deliveries</h3> 
            </div>

            <!-- Second Item -->
            <div class="item">
                <i class="far fa-map icon"></i>
                <h3>Find stores near you</h3>
            </div>

            <!-- Third Item -->
            <div class="item">
                <i class="fas fa-dollar-sign icon"></i>
                <h3>Best prices guarranteed</h3>
            </div>

            <!-- Fourth item -->
            <div class="item">
                <i class="far fa-credit-card icon"></i>
                <h3>All credit card accepted</h3>
            </div>

        </div>
    </div>
</div>
  
</template>

<script>
export default {
    name:'HighlightedContent'
}
</script>

<style lang="scss" scoped>
@import '../style/mixins.scss';
@import '../style/vars.scss';

.overlay{
    @include flex-cc;
    width: 100%;
    background-image: linear-gradient(#26422900,$dark-green);

    .row{
        height: 100%;
        @include flex-between;

        .item{
            @include flex-cc;
            flex-direction: column;
            color:white;

            .icon{
                font-size: 55px;
            }
            
            h3{
                padding-top: 30px;
                color:$salvia-green;
                font-weight: 400;
            }
    
        }
    }
}

</style>
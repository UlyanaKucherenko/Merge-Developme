<template>
  <div class="sing-page">
    <div class="container sing-page__container">
      <div class="sing-page__col-left">
        <promo-sliders />
      </div>

      <div class="sing-page__col-right">
         <!--Sing form -->
        <sing-form />
      </div>
      
    </div>
  </div>
</template>

<script>
import PromoSliders from './PromoSliders.vue'
import SingForm from './SingForm.vue'
export default {
  name: 'SingPage',
  components: {
    PromoSliders,
    SingForm
  }
}
</script>
<style lang="scss">
  .sing-page {
    min-height:100vh;
    
    &__container {
      @include flex(center,center,row,wrap);
       height: 100vh;
       padding: 0 20px;
        @include media(768px) {
           @include flex(center,center,column);
            padding: 0;
            height: 100%;
        }
    }
    &__col-left {
      width: 55%;
      position: relative;
      height: 100%;
      padding: 20px;
      @include media(768px) {
        width: 100%;
      }

    }
    &__col-right {
      width: 45%;
      height: 100%;
      @include media(768px) {
        width: 100%;
      }
    }


  }
</style>
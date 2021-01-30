<template>
    <div class="promo-sliders">
         <a-carousel  arrows dots-class="slick-dots slick-thumb"
         :autoplaySpeed="5000"
         :speed="1000">
            <div class="promo-sliders__slide" v-for="{image, title, text} in slides" :key="title">
                <div class="promo-sliders__slide-wrap-shadow">
                    <div class="promo-sliders__slide-wrap-image">
                        <img  :src="require(`@/assets/img/slides/${image}.png`)" :alt="image">
                    </div>
                </div>    
                <div>
                    <h2 class="promo-sliders__title">{{title}}</h2>
                    <p class="promo-sliders__text" >{{text}}</p>
                </div>
                
            </div>
        </a-carousel>
    </div>
</template>
<script>
export default {
    name: "PromoSliders",
    
    props:{
        title: {
            type: String,
            default: "default title"
        },
        text: {
            type: String,
            default: "default text"
        },
    },

    data() {
        return{

            slides: [
                {
                    image: "slide1",
                    title: "Tokenplace",
                    text: "Multi-exchange Trading Terminal"
                },
                 {
                    image: "slide2",
                    title: "Fund Platform",
                    text: "Hedge funds wealth management"
                    
                },
                 {
                    image: "slide3",
                    title: "Noviscient",
                    text: "Management Platform"
                },
               
            ],
        }
    },
}
</script>
<style lang="scss" >

    .promo-sliders {
        background-color: $blue;
        max-width: 800px;
        min-height: 610px;
        padding: 20px 0 ;
        height: 100%;
        width: 100%;
        border-radius: 20px;
        @include flex(center, center, column);
        position: relative;

         &:before {
            content: "";
            position: absolute;
            @include position(0,0,0,0);
            display: block;
            background: url("../assets/img/graphics.svg") no-repeat center;
            background-size: cover;
            z-index: 0;
            border-radius: 20px;
            }
             @include media(768px) {
               min-height: 560px;
            }

        & .ant-carousel  {
            text-align: center;
            overflow: hidden;
            max-width: 512px;
            width: 100%;

            }   

        & .ant-carousel .slick-dots {
            height: 8px;
        }

        & .ant-carousel .slick-dots-bottom {
            bottom: 0px;
        }

        & .ant-carousel .slick-dots li  {
            margin-right: 45px;
            &:last-child {
                margin-right: 0;
            }
        }
        & .ant-carousel .slick-dots li button {
            width: 8px;
            height: 8px;
            background: $white;
            border-radius: 50%;
        }

        &__slide-wrap-shadow {
            margin-bottom: 80px;
            padding: 0 40px;  

            @include media(768px) {
                padding: 0 24px; 
            }
        }

        &__slide-wrap-image{
            @include padding-hack(58%, cover); 
            box-shadow: 0 45px 26px rgba(0, 46, 123, 0.7), 0 10px 10px rgba(0, 46, 123, 0.7);
            &:first-child {
                @include padding-hack(56%, cover); 
            }
        }

        &__title {
            @include text($second-font-size,600,#fff);
            margin-bottom: 15px;
            text-align: center;
        }

        &__text {
            @include text($text-font-size,600,#fff);
            text-align: center;
            margin-bottom: 84px;
        }
    }
</style>

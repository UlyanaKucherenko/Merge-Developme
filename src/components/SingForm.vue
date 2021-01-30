<template>
    <div class="sing-form">
        <x-logo class="sing-form__logo" />
        <div class="sing-form__form-content">
            <h2 class="sing-form__title">Sing in</h2>
            <p class="sing-form__subtitle"> Don’t have an account?
                <a href="#" target="_blank" class="sing-form__link-singup">
                    Sing up now
                </a>
            </p>

            <!--Form-->
            <a-form class="sing-form__form-sigin"
                :form="form"
                @submit="handleSubmit" >
                <a-form-item 
                label="Email">
                    <a-input
                        v-decorator="[
                        'email',
                        { rules: [{ required: true, message: 'Invalid email' }] },
                        ]"
                        type="email" >
                    </a-input>
                </a-form-item>
                <a-form-item 
                label="Password">
                    <a-input
                        v-decorator="[
                        'password',
                        { rules: [{ required: true, message: 'Invalid format too short' }] },
                        ]"
                        type="password">
                    </a-input>
                    <a class="sing-form__form-forgot" href="#" target="_blank" >
                        Forgot your password?
                    </a>
                </a-form-item>
                <a-form-item>
                
                <a-button type="primary" html-type="submit" class="sing-form__form-button">
                    Sing in
                </a-button>
                </a-form-item>
            </a-form>   
        </div>

         <!--Info links-->
        <ul  class="sing-form__list-info">
            <li class="sing-form__list-item" v-for="item in infoLinks" :key="item">
                <a class="sing-form__list-item-link" href="#" target="_blank" >
                    {{item}}
                </a>
            </li>
        </ul>
    </div>
</template>
<script>
import XLogo from './common/icons/XLogo.vue'

export default {
    name:"SingForm",
    components: {
        XLogo
    },
    
    data() {
        return{
            infoLinks: [
                "Contact",
                "Privacy",
                "Terms"
            ],
        }
    },

    beforeCreate() {
    this.form = this.$form.createForm(this, { name: 'singIn' });
  },

  methods: {

    handleSubmit(e) {
      e.preventDefault();
        console.log('Received values of form: ');
    },

  },
}
</script>
<style lang="scss">
    .sing-form {
        width: 100%;
        max-width: 600px;
        max-height: 800px;
        height: 100%;
        padding: 30px 70px 20px 60px;
        @include flex(flex-start, flex-start, column);
        position: relative;

        @include media($screen: $screen-desktop) {
            padding: 30px 30px 20px 30px;
        }
         @include media(768px) {
            width: 100%;
          @include flex(center, center, column);
          margin: 0 auto;
          padding: 10px 20px;
        }

        &__logo {
            text-align: left;
            margin-bottom: 50px;
             @include media(768px) {
                margin-bottom: 20px;
            }
        }

        &__form-content {
            max-width: 420px;
            width: 100%;
            position: relative;
             @include media(768px) {
                margin-bottom: 25px;
            }
        }

        &__title {
            @include text($first-font-size, 700, $grey-dark);
            margin-bottom: 15px;
        }

        &__subtitle {
            @include text($text-font-size, 600, $grey-dark);
            margin-bottom: 60px;
             @include media(768px) {
                margin-bottom: 20px;
            }
        }

        &__form-sigin .login-form {
            max-width: 420px;
            width: 100%;
            @include flex( center, center, column, wrap);
            width: 100%;
            text-align: left;
        }
        &__form-sigin .sing-form__form-forgot {
            position: absolute;
            right: 10px;
            top: -10px;
            @include text($text-font-size, 600, $grey-light);

             &:hover {
                color: rgba(#333333, 1)
            }
            
        }

        & .ant-form-explain {
            position: absolute;
            top: -28px;
            right: 0;
            @include text($error-font-size, 600, $error-color);
        }    

        & .ant-form-item {
            &:last-child {
                margin-bottom: 0;
            }
        }

         & .ant-form-item-required::before,
          .ant-form-item-label > label::after {
            display:none;
        }

        & .ant-form-item label {
            @include text($text-font-size, 600, $grey-dark);
        } 

        &__form-sigin input,
        &__form-sigin .sing-form__form-button {
            min-height: 54px;
            padding: 0 10px;
            max-width: 420px;
            width: 100%;
            border-radius: 8px;
            @include text($text-font-size, 600, $grey-dark);
        }

        &__form-sigin input[type='password'] {
            padding-right: 60%;
            position: relative;
        }

        &__form-sigin .sing-form__form-button {
            @include text(16px, 400, $white);
            background-color: $blue;
            box-shadow: 0 14px 28px rgba($blue,0.25), 0 10px 10px rgba($blue,0.22);
            margin: 0;

            &:hover {
                background-color: $hover-element;
            }
            &:active {
                background-color: #065BEA;
            }

            &:disabled {
                @include text(16px, 400, $white);
                background-color: #C6D0E0;
                box-shadow: none;
            }

        }


        &__list-info {
            @include flex( flex-start, center, row, wrap);
            position: absolute;
            bottom: 70px;

            @include media(768px) {
                position: static;
                bottom: 0px;
                @include flex( center, center, row, wrap);
                width: 100%;
            }
        }

        &__list-item {
            margin-right: 25px;

            &:last-child{
                margin-right: 0;
            }
        }

        &__list-item-link {
            @include text($text-font-size, 600, $grey-light);
              &:hover {
                color: rgba(#333333, 1)
            }
        }
    }
</style>
<template>
    <div id="register_panel">
        <div id="register_panel_form">
            <RegisterForm
                    :list="registerList"
                    store-name="registerForm"
                    store-status-name="registerFormStatus"/>
        </div>
        <HyperLink :list="registerInHyperLink"/>
        <div class="button_container">
            <FormButton
                    :click-handler="clickHandler"
                    content="sign up"
                    :status="isLoading"/>
        </div>
    </div>
</template>

<script>
    import { registerList, registerInHyperLink } from '../config/list.config';
    import RegisterForm from './elements/Form';
    import HyperLink from './elements/HyperLink';
    import FormButton from './elements/FormButton';
    export default {
        name: 'RegisterPanel',
        data: function () {
            return {
                registerList,
                registerInHyperLink
            };
        },
        components: {
            RegisterForm,
            HyperLink,
            FormButton
        },
        methods: {
            clickHandler: function () {
                console.log(213);
                this.isLoading = true;
            }
        },
        computed: {
            isLoading: {
                get: function () {
                    return this.$store.state.isLoading;
                },
                set: function (value) {
                    this.$store.commit('updateGlobalState', {
                        key: 'isLoading',
                        value: value
                    });
                }
            }
        }
    };
</script>

<style lang="scss">
    #register_panel {
        padding: 66px 0 36px;
        #register_panel_form {
            display: flex;
            justify-content: center;
        }
        .button_container {
            padding: 0 126px 0 121px;
        }
    }
</style>

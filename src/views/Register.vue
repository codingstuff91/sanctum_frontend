<template>
    <div class="container">
        <b-notification type="is-primary" aria-close-label="Close notification">
            Inscrivez vous sur cette plateforme, pour apprendre a utiliser Laravel SANCTUM
        </b-notification>

        <section>
            <div class="columns">
                <div class="column is-half">
                    <img alt="logo" src="../assets/laravel-sanctum.png">
                </div>
                <div class="column"> 
                    <div class="column is-full">
                        <b-field label="Username" label-position="on-border">
                            <b-input value="johnsilver" v-model="user.username"></b-input>
                        </b-field>
                    </div>

                    <div class="column is-full">
                        <b-field label="Email" label-position="on-border">
                            <b-input type="email" v-model="user.email"></b-input>
                        </b-field>
                    </div>

                    <div class="column is-full">
                        <b-field label="Password" label-position="on-border">
                            <b-input type="password" 
                                v-model="user.password">
                            </b-input>
                        </b-field>
                    </div>
                </div>
            </div>

            <b-button type="is-success" @click="register" class="mt-6">Inscription</b-button>

        </section>
    </div>
</template>

<script>
import axios from 'axios'

const BASE_URL = "http://localhost:8000/api"

    export default {
        data() {
            return {
                user: {}
            }
        },
        methods: {
            register() {
                axios.post(BASE_URL + '/user', {
                    user : this.user
                }).then(()=>{
                    this.$buefy.dialog.confirm({
                        title: 'Succès',
                        message: 'Nouveau compte utilisateur crée !!',
                        confirmText: 'Fermer',
                        type: 'is-success',
                        hasIcon: true                    
                    })
                }).catch((error)=> {
                    console.log(error);
                    this.$buefy.dialog.alert({
                        title: 'Error',
                        message: error.message,
                        type: 'is-danger',
                        hasIcon: true,
                        icon: 'times-circle',
                        iconPack: 'fa',
                        ariaRole: 'alertdialog',
                        ariaModal: true
                    })                
                })
            }
        },
    }
</script>

<style lang="scss" scoped>

</style>
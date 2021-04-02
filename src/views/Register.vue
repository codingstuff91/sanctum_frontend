<template>
    <div>
        <form @submit.prevent="register">
            <label>Username</label>
            <input type="text" v-model="user.username">

            <label>Email</label>
            <input type="text" v-model="user.email">

            <label>Password</label>
            <input type="text" v-model="user.password">

            <input type="submit" value="inscription">
        </form>
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
                }).then((response)=>{
                    localStorage.setItem('test-token', response.data.Token)
                }).catch((error)=> {
                    console.log(error.response.data.errors)
                })
            }
        },
    }
</script>

<style lang="scss" scoped>

</style>
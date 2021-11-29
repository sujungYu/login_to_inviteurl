<template>
  <div>
      <input type="text" placeholder="아이디" v-model="id"><br>
      <input type="password" placeholder="비밀번호" v-model="pw" v-on:keyup.enter="login"><br>
      <button v-on:click="login">login</button>
  </div>
</template>

<script>
import axios from 'axios'
export default {
    data: function() {
        return{
                id: '',
                pw: ''
        }
    },
    methods: {
        login: function() {
            const url = 'http://localhost:8000/users';
            const data = {
                username: this.id,
                password: this.pw
            }
            axios.post(url, data).then((res) => {
                localStorage.setItem("user", res.data.username);
                this.$router.push('./');
            })
            .catch((error) => {
                console.log(error);
            })
        }
    }

}
</script>

<style>

</style>
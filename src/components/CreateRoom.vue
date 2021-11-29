<template>
  <div>
      <input placeholder="방 이름을 입력하세요" v-model="roomname" type="text" >
      <button v-on:click="cancell">취소</button>
      <button v-on:click="create">생성</button>
  </div>
</template>

<script>
import axios from "axios";
export default {
    data: function() {
        return {
            roomname: ''
        }
    },
    methods: {
        cancell: function() {
                this.$router.go(-1) //한단계 뒤로
        },
        create: function() {
             var url = 'http://localhost:8000/room';
             var data = {
                 roomname: this.roomname,
                 manager: localStorage.getItem("user")
             }
             console.log(data);
              axios.post(url,data).then((res) => {
                //  console.log(res);
                 this.$router.push(`/room/${res.data.id}`)
                //  this.acceptInvitation(response.data.id)
             }).catch((error) => {
                console.log(error);
            })


        },
    }
}
</script>

<style>

</style>
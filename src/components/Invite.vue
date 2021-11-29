<template>
  <div>
      <button v-on:click="createinvitetoken">초대링크생성</button>
      <input v-model="inviteurl" placeholder="아래 링크를 복사하여 멤버를 초대하세요." type="text">
  </div>
</template>

<script>
// import axios from 'axios'
export default {
    data: function() {
        return {
            token:null,
            inviteurl: "",
            roomid: ""
        }
    },
    computed: {
      invitetoken() {
        return this.token
        }  
    },
    watch: {
    invitetoken (val) {
      this.inviteurl = `http://localhost:8080/n/${val}`
    }
  },
    
    // created: function() {
    //     const url = 'http://localhost:8000/room';
    //     axios.get(url).then((res) => {
    //         this.roomid = res.data;
    //         console.log(this.roomlid);
    //     }).catch((error) => {
    //             console.log(error);
    //         })

    // },
    methods: {
        createinvitetoken: function() {
            this.token = Math.random().toString(36).substring(2, 15) + Math.random().toString(36).substring(2, 15);
            // this.roomid = 
            // const url = `http://localhost:8000/room/${}`

        }
    }

}
</script>

<style>

</style>
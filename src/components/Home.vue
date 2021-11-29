<template>
  <div>
      <router-link to="/createroom" tag="span" style="cursor: pointer">
      방만들기
      </router-link>
      <ul>
          <li v-for="roomlist in roomlists" v-bind:key="roomlist.roomname">
              {{roomlist.roomname}}
          </li>
      </ul>

      <!-- <router-link :to=""></router-link> -->
  </div>
</template>

<script>
import axios from 'axios'
export default {
    data: function() {
        return {
            roomlists: []
        }
    },
    created: function() {
        const url = 'http://localhost:8000/room';
        // const data = {
        //     params: {
        //         roomname: []
        //     }
        // }
        axios.get(url).then((res) => {
            this.roomlists = res.data;
            console.log(this.roomlists);
        }).catch((error) => {
                console.log(error);
            })
    }

}
</script>

<style>

</style>
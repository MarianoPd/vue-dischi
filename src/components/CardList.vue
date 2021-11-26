<template>
  <div>
      <Card/>
  </div>
</template>

<script>

import axios from 'axios';
import Card from './Card.vue'

export default {
    name: 'CardList',
    components:{
        Card,
    },

    data(){
        return{
            albums: [],
            loaded: false,
            apiUrl: 'https://flynn.boolean.careers/exercises/api/array/music',
        }
    },

    methods:{
    getApi(){
      axios.get(this.apiUrl)
        .then( response => {
          this.characters = response.response;
          this.loaded = true;
        })
        .catch( e => {
          console.log(e);
        })
    }
    },

    mounted(){
        this.getApi();
    }
}
</script>

<style lang="scss" scoped>

</style>
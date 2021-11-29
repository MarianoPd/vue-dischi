<template>
  <div v-if="loaded" class="row" >
      <Card
        v-for="(album, index) in albums"
        :key="index"
        :album="album"
      />
  </div>
  <div v-else>
    <Loader />
  </div>
</template>

<script>

import axios from 'axios';
import Card from './Card.vue';
import Loader from './Loader.vue';

export default {
    name: 'CardList',
    components:{
        Card,
        Loader,
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
        .then( r => {
          this.albums = r.data.response;
          this.loaded = true;
        })
        .catch( e => {
          console.log('errore axios',e);
        })
    }
    },

    mounted(){
        this.getApi();
    }
}
</script>

<style lang="scss" scoped>
    div{
        padding:80px 0 80px 0;
    }
</style>
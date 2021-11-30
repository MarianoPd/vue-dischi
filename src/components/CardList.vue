<template>
  <div v-if="loaded" class="row" >
      <Card
        v-for="(album, index) in filteredAlbums"
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
    props:{
      selectGenere: String,
    },

    data(){
        return{
            albums: [],
            genres: [],
            loaded: false,
            apiUrl: 'https://flynn.boolean.careers/exercises/api/array/music',
        }
    },

    computed:{
      filteredAlbums(){
        if(this.selectGenere === ''){
          return this.albums;
        }
        return this.albums.filter(album => album.genre === this.selectGenere);
      }
    },

    methods:{
    getApi(){
      axios.get(this.apiUrl)
        .then( r => {
          this.albums = r.data.response;
          this.loaded = true;
          this.albums.forEach(album => {
            if(!this.genres.includes(album.genre)) this.genres.push(album.genre);
          });
          console.log('cardList', this.genres );
          this.$emit('genresList',this.genres);
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
<template>
  <div>
    <div v-if="loaded && selectSelection === 'author'" class="row" >
      <Card
        v-for="(album, index) in filteredByAuthor"
        :key="index"
        :album="album"
      />
  </div>
  <div v-if="loaded && selectSelection === 'genre'" class="row" >
      <Card
        v-for="(album, index) in filteredByGenre"
        :key="index"
        :album="album"
      />
  </div>
  <div v-else>
    <Loader />
  </div>
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
      selectAuthor: String,
      selectSelection: String,
    },

    data(){
        return{
            albums: [],
            genres: [],
            authors: [],
            loaded: false,
            apiUrl: 'https://flynn.boolean.careers/exercises/api/array/music',
        }
    },

    computed:{
      filteredByGenre(){
        if(this.selectGenere === '')return this.albums;
        return this.albums.filter(album => album.genre === this.selectGenere);
      },
      filteredByAuthor(){
        if(this.selectAuthor === '') return this.albums;
        return this.albums.filter(album => album.author === this.selectAuthor);
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
          this.$emit('genresList',this.genres);

          this.albums.forEach(album =>{
            if(!this.authors.includes(album.author)) this.authors.push(album.author);
          });
          this.$emit('authorList',this.authors);
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
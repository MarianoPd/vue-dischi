<template>
  <div class="main-wrapper">
    <Header @changeGenre="setGenre" :genreList='genres' 
            @changeAuthor="setAuthor" :authorsList='authors'/>
    <div class="container">
      <Card-List :selectGenere="genre" @genresList='setGenresList'
                :selectAuthor="author" @authorList='setAuthors' />
    </div>
  </div>
</template>

<script>

import Header from './components/Header.vue';
import CardList from './components/CardList.vue'

export default {
  name: 'App',
  components: {
    Header,
    CardList,
  },
  data(){
    return{
      genre: '',
      genres: [],
      author: '',
      authors: [],
    }
  },
  methods:{
    setGenre(text){
      this.genre = text;
      console.log('app', this.genre);
    },
    setGenresList(array){
      this.genres = array;
      console.log('app array', this.genres);
    },
    setAuthor(text){
      this.author = text;
    },
    setAuthors(array){
      this.authors = array;
      console.log('app array authors', this.authors);
    }
  }
}
</script>

<style lang="scss">

@import './assets/style/vars.scss';
@import './assets/style/generals.scss';

.main-wrapper{
  min-height: 100vh;
  background-color: $primary-color-dark;
}

</style>

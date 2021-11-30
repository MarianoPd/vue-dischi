<template>
  <div class="main-wrapper">
    <Header @changeGenre="setGenre"/>
    <div class="container">
      <Card-List :selectGenere="genre" />
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
    }
  },
  methods:{
    setGenre(text){
      this.genre = text;
      console.log('app', this.genre);
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

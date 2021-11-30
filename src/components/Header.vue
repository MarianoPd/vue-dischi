<template>
  <div class="d-flex justify-content-between">
    <img src="../assets/img/Spotify_logo.png" alt="icon">
    <div>
      <select v-model="author" @change="changeByAuthor()">
          <option value="" selected>Select author</option>
          <option v-for="(auth, index) in authorsList"
            :key="index"
            :value="auth" >{{auth}}</option>
          
      </select>
      <select v-model="genre" @change="changeByGenre()">
          <option value="" selected>Select genre</option>
          <option v-for="(genre, index) in genreList"
            :key="index"
            :value="genre" >{{genre}}</option>
          
      </select>
    </div>
  </div>
</template>

<script>

export default {
    name: 'Header',
    props:{
      genreList: Array,
      authorsList: Array,
    },
    data(){
      return{
        genre: '',
        author: '',
        selection: 'author',
      }
    },
    methods:{
      changeByAuthor(){
        this.$emit('changeAuthor', this.author);
        this.selection = 'author';
        this.$emit('changeSelection', this.selection);
      },
      changeByGenre(){
        this.$emit('changeGenre', this.genre);
        this.selection = 'genre';
        this.$emit('changeSelection', this.selection);
      }
    }
}
</script>

<style lang="scss" scoped>
@import '../assets/style/vars.scss';
@import '../assets/style/generals.scss';
@import '../assets/style/mixins.scss';
div{
    height: 70px;
    background-color: $primary-color;
    @include center(align);
    img{
        width: 45px;
        aspect-ratio: 1;
        margin-left: 20px;
    }
    select{
        margin-right: 100px;
        min-width: 150px;
    }
}

</style>
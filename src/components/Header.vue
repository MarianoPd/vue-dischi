<template>
  <div class="d-flex justify-content-between">
    <img src="../assets/img/Spotify_logo.png" alt="icon">
    <div>
      <select v-model="genre" @change="$emit('changeGenre', genre)">
          <option value="" selected></option>
          <option value="Rock">Rock</option>
          <option value="Pop">Pop</option>
          <option value="Jazz">Jazz</option>
          <option value="Metal">Metal</option>
          
      </select>
    </div>
  </div>
</template>

<script>

export default {
    name: 'Header',
    components:{
      
    },
    data(){
      return{
        genre: '',
        genres: [],
      }
    },
    methods:{
     

      
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
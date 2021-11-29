<template>
  <div class="d-flex justify-content-between">
    <img src="../assets/img/Spotify_logo.png" alt="icon">
    <div>
      <SelectGenre @genre="setGenre"/>
    </div>
  </div>
</template>

<script>
import SelectGenre from './SelectGenre.vue'
export default {
    name: 'Header',
    components:{
      SelectGenre,
    },
    data(){
      return{
        genre: '',
      }
    },
    methods:{
      setGenre(text){
        this.genre = text;
         
        this.$emit('genre', this.genre);
        console.log(this.genre);
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
}

</style>
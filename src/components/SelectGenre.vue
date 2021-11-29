<template>
  <div>
      <select v-model="genre" :onchange='sendGenre'>
          <option value="Rock">Rock</option>
          <option value="Pop">Pop</option>
          <option value="Jazz">Jazz</option>
          <option value="Metal">Metal</option>
          
      </select>
  </div>
</template>

<script>


export default {
    name: 'Select',
    data(){
        return{
            genre: '',
        }
    },
    methods:{
        sendGenre(){
            this.$emit('genre', this.genre)
        }
    },
    mounted(){
       
    },

}
</script>

<style lang="scss" scoped>
@import '../assets/style/vars.scss';
@import '../assets/style/mixins.scss';

    select{
        margin-right: 100px;
        min-width: 150px;
    }
</style>
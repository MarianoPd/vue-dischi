<template>
  <div class="col-2 card">
      <img :src="album.poster" :alt="album.title">
      <h3>{{album.title}}</h3>
      <h5>{{album.author}}</h5>
      <p>{{album.year}}</p>
  </div>
</template>

<script>
export default {
    name: 'Card',
    props:{
        album: Object,
    }
}
</script>

<style lang="scss" scoped>
@import '../assets/style/vars.scss';
    .card{
        margin: 20px;
        background-color: $primary-color;
        padding: 20px;
        padding-bottom: 0;
        text-align: center;
        img{ 
            width: 100%;
        }
        h3{
            color: white;
            margin-top: 25px;
            font-weight: 700;
        }
        h5{
            margin-top: 30px;
        }
        h5,p{
            color: #80807b;
            font-weight: 600;
        }
      
    }
</style>
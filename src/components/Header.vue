<template>
  <div >
    <img src="../assets/img/Spotify_logo.png" alt="icon">
  </div>
</template>

<script>
export default {
    name: 'Header',
}
</script>

<style lang="scss" scoped>
@import '../assets/style/vars.scss';
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
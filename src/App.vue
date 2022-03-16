<template>
  <vue-selfie @picture-taken="imageSrc = $event" />
  <img :src="imageSrc" />
</template>

<script>
import VueSelfie from './components/VueSelfie'

export default {
  name: 'App',
  components: {
    VueSelfie
  },
  data(){
    return{
      imageSrc : null 
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

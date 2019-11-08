<template>
  <div id="app">
    <GetImage btnName="멍멍" @getAnimalImage="getImage"/>
    <GetImage btnName="야옹" @getAnimalImage="getImage"/>
    <img :src="animalUrl">
  </div>
</template>

<script>
import GetImage from './components/GetImage.vue'
import axios from 'axios'

export default {
  name: 'app',
  components: {
    GetImage,
  },
  data: function() {
    return {
      animalUrl: '',
    }
  },
  methods: {
    getImage: function (name) {
      if (name === '멍멍'){
        const DOG_URL = 'https://dog.ceo/api/breeds/image/random'
        axios.get(DOG_URL)
          .then(response => this.animalUrl = response.data.message)
          .catch(error => console.log(error))
      } else {
        const CAT_URL = 'https://api.thecatapi.com/v1/images/search'
        axios.get(CAT_URL)
          .then(response => this.animalUrl = response.data[0].url)
          .catch(error => console.log(error))
      }
    }
  },
  
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

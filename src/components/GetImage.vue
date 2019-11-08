<template>
  <button @click="onAnimalImage()">{{btnName}}</button>
</template>

<script>
export default {
  props: {
    btnName: String,
  },
  methods: {
    onAnimalImage: function () {
      this.$emit('getAnimalImage', this.btnName)
    }
  }
}
</script>

<style>

</style>
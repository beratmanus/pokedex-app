<template>
  <p>pokemon id is {{id}}</p>
  <p>Name is {{name}}</p>
  <img :src=img alt="">
</template>

<script>
export default {
  props: ['id' , 'name' , 'img'],
  data() {
    return {
    }
  },
  
}
</script>

<style>

</style>
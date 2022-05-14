<template>
<div>
  <h1 class="text-left p-4 text-4xl capitalize font-bold">{{name}}</h1>
  <img :src=img alt="">
</div>
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
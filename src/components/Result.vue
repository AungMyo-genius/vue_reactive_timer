<template>
  <div>
    <p>The result is {{score}}ms</p>
  <div v-if="score<300">
      <p>You are too fast! </p>
  </div>
  <div v-else-if="score>300 && score<600">
      <p>You are Normal</p>
  </div>
  <div v-else>
      <p>You are too slow!</p>
  </div>
  </div>
</template>

<script>
export default {
  props:['score'],
}
</script>

<style>

</style>
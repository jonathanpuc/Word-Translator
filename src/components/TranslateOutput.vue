<template>
  <h2 class="text-success">{{translatedText}}</h2>
</template>

<script>


export default {
  name: 'translateOutput',
  props: ['translatedText']
  }
</script>

<style>
h2 {
    font-family: 'Anton', sans-serif;

}
</style>

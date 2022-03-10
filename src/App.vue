<template>
    <h1> {{ message }} </h1>
    <button @click="count++"> {{ count}}</button>
</template>

<script>
  export default {
    data() {
      return {
        message:"Hello",
        count: 0
      }
    }
  }
</script>


<style>
@import './assets/base.css';

</style>

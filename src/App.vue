<template>
    <h1> {{ message }} </h1>
    <button @click="increment"> {{ count }}</button>
</template>

<script>
  export default {
    data() {
      return {
        message:"Hello",
        count: 0
      }
    },
    methods: {
      increment(){
        this.count++
      }
    },
    mounted(){
      this.increment();
    }
  }
</script>


<style>
@import './assets/base.css';

</style>

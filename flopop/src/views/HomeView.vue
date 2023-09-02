<template>
  <div class="Home">
     <h1 class="Title">FloPoP</h1>
     <Todolist/>
  </div>
</template>

<style>
  .Title {
    text-align: center;
    font-size: 8vh;
  }
</style>

<script lang="ts">
import { defineComponent } from 'vue';
import Todolist from '../components/home/Todolist.vue';

export default defineComponent({
  name: 'HomeView',
  components: {
    Todolist
  },
});
</script>

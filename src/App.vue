<template>
  <div id="app">
    <todoTasklist>

    </todoTasklist>
  </div>
</template>

<script>
import todoTasklist from './components/todoTasklist.vue'


export default {
  name: 'App',
  components: {
    "todoTasklist": todoTasklist,
  }
}
</script>

<style>
  body{
    margin: 0;
    padding: 0;
    text-decoration: none;
    font-family: Avenir,Helvetica,Arial,sans-serif;
    font-size: 20px;
  }

  #app{
    position: relative;
    display: flex;
    align-items: center;
    justify-content: center;
    background-image: url(./assets/image1.jpg);
    background-size: cover;
    height: 100vh;
  }
</style>

<template>
  <div id="app" class="container">
    <div class="jumbotron jumbotron-fluid">
      <div class="container-fluid">
        <h1>MONSTER GAME</h1>
        <p>Un golpe es tuyo, el otro del montruo. Veamos quien gana!</p>
      </div>
    </div>

    <div class="jumbotron jumbotron-fluid">
    <Juego />
    </div>
    

  </div>
</template>

<script>
import Juego from './components/Juego.vue'
export default {
  name: 'App',
  components: {
    Juego,
 
  }
}
</script>

<style>

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #0a0a0a;
  margin-top: 60px;
}

.jumbotron{
  background-color: rgb(230, 215, 196);
}

h1 {
  color: rgb(6, 6, 53);
}

</style>

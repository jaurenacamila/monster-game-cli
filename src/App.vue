<template>
  <div id="app" class="container">
    <div class="jumbotron jumbotron-fluid">
      <div class="container-fluid">
          <h1>Monster Game</h1>
          <p>Un golpe es tuyo, el otro del montruo. Veamos quien gana!</p>
      </div>
    </div>

    <Juego />
    <div class="row">
      <div class="div">
    <Barra nombreBarra="Barra Jugador" />
    </div>
    <div class="div">
    <Barra nombreBarra="Barra Monstruo"/>
    </div>
    </div>
    

  </div>
</template>

<script>
import Juego from './components/Juego.vue'
import Barra from './components/Barra.vue'

export default {
  name: 'App',
  components: {
    Juego,
    Barra
  }
}
</script>

<style>

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.jumbotron{
  background-color: rgb(230, 215, 196);
}

h1 {
  color: rgb(6, 6, 53);
}

</style>

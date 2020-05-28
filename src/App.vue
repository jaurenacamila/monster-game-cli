<template>
  <div id="app" class="container">
    <div class="jumbotron jumbotron-fluid">
      <div class="container-fluid">
        <h1>Monster Game</h1>
        <p>Un golpe es tuyo, el otro del montruo. Veamos quien gana!</p>
      </div>
    </div>

    <div class="jumbotron jumbotron-fluid">
    <Juego />
    </div>

   <!--  <div class="jumbotron jumbotron-fluid">
      <div class="row">
        <Barra nombreBarra="Barra Jugador" color=red :salud=100 icono="fa-angry"  />
        <Barra nombreBarra="Barra Monstruo" color=blue :salud=100 icono="../assets/imgs/monstruo1.png" />
      </div>
    </div>

    <div class="jumbotron jumbotron-fluid">
      <Botones />
    </div>
    
    <div class="jumbotron jumbotron-fluid">
      <Logs :turnos="turnos" />
    </div> -->
    

  </div>
</template>

<script>
import Juego from './components/Juego.vue'
/* import Barra from './components/Barra.vue'
import Botones from './components/Botones.vue'
import Logs from './components/Logs.vue'
 */
export default {
  name: 'App',
  components: {
    Juego,
 /*    Barra,
    Botones,
    Logs */
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

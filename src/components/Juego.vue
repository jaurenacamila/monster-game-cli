<template>
  <section class="src-components-juego">
    <h1>Juego</h1>

     <section class="row">
        <div class="small-6 columns">
            <Barra :salud="saludJugador" icono="fa-angry" color="goldenrod" />
        </div>
        <div class="small-6 columns">
            <Barra :salud="saludMonstruo" icono="fa-pastafarianism" color="rgb(3, 110, 12)"/>
        </div>
    </section>
    <hr>

    <Botones 
        :hayUnaPartidaEnJuego="hayUnaPartidaEnJuego"
        :empezarPartida="empezarPartida"
        :atacar="atacar"
        :ataqueEspecial="ataqueEspecial"
        :curar="curar"
        :terminarPartida="terminarPartida" />

    <hr>

         <Logs :turnos="turnos" />

    
  </section>
</template>

<script>

import Barra from './Barra.vue'
import Botones from './Botones.vue'
import Logs from './Logs.vue'

  export default  {
    name: 'src-components-juego',
    components: {
      Barra,
      Botones,
      Logs
    },
    props: [],
    mounted () {

    },
    data () {
      return {
        saludJugador: 100,
        saludMonstruo: 100,
        hayUnaPartidaEnJuego: false,
        turnos: [],
        esJugador: false,
        rangoAtaque: [3, 10],
        rangoAtaqueEspecial: [10, 20],
        rangoAtaqueDelMonstruo: [5, 12],

      }
    },
    methods: {

        empezarPartida: function () {
            this.hayUnaPartidaEnJuego = true;
            this.saludJugador = 100;
            this.saludMonstruo = 100;
            this.turnos = [];
        },

         atacar: function () {
            var heridas = this.calcularHeridas(this.rangoAtaque);
            this.saludMonstruo -= heridas;
            this.turnos.unshift({
                esJugador: true,
                text: 'El jugador golpea por: ' + heridas
            });
            if (this.verificarGanador()){
                return;
            }
            this.ataqueDelMonstruo();
        },

           ataqueEspecial: function () {
            var heridas = this.calcularHeridas(this.rangoAtaqueEspecial);
            this.saludMonstruo -= heridas;
            this.turnos.unshift({
                esJugador: true,
                text: 'El jugador golpea por: ' + heridas
            });
            if (this.verificarGanador()){
                return;
            }
            this.ataqueDelMonstruo();
        },

        curar: function () {
            if(this.saludJugador <= 90){
                this.saludJugador += 10;
            }else {
                this.saludJugador = 100;
            }
            this.turnos.unshift({
                esJugador: true,
                text: 'El jugador está sanando +10 '
            });
            this.ataqueDelMonstruo();
        },

        registrarEvento(evento) {
          this.turnos.unshift(evento);
      },

        terminarPartida: function () {
            this.hayUnaPartidaEnJuego = false;
            this.turnos = [];
        },

        ataqueDelMonstruo: function () {
            var heridas = this.calcularHeridas(this.rangoAtaqueDelMonstruo);
            this.saludJugador -= heridas;
            this.turnos.unshift({
                esJugador: false,
                text: 'El monstruo golpea por: ' + heridas
            });
            this.verificarGanador();
        },

        calcularHeridas: function (rango) {
            let min = rango[0];
            let max = rango[1];
            return Math.max(Math.floor(Math.random()* max) + 1, min);
        },

        verificarGanador: function () {
            if (this.saludMonstruo <= 0){
                if (confirm("Ganaste esta partida. Querés jugar de nuevo?")){
                    this.empezarPartida();
                }else {
                    this.empezarPartida = false;
                }
                return true;
            }else if(this.saludJugador<=0){
                if(confirm("Perdiste! Querés jugar de nuevo?")){
                    this.empezarPartida();
                }else{
                    this.empezarPartida = false;
                }
                return true;
            }
            return false;
        },
    
    },
    computed: {

    }
}
</script>

<style scoped lang="css">
  .src-components-juego {

  }

img {
    border-radius: 10px;
    box-shadow: 2px 2px 2px rgba(0, 0, 0, 0.5);
}

</style>
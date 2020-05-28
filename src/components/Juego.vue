<template>

  <section class="src-components-juego">
    <h1>Juego</h1>
    
  </section>

</template>

<script lang="js">

  export default  {
    name: 'src-components-juego',
    props: [],
    mounted () {

    },
    data () {
      return {
         hayUnaPartidaEnJuego: false,
         esJugador: false,
        rangoAtaque: [3, 10],
        rangoAtaqueEspecial: [10, 20],
        rangoAtaqueDelMonstruo: [5, 12],

      }
    },
    methods: {
       getSalud(salud) {
            return `${salud}%`
        },
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
         cssEvento(turno) {
            //Este return de un objeto es prque vue asi lo requiere, pero ponerlo acá queda mucho mas entendible en el codigo HTML.
            return {
                'player-turno': turno.esJugador,
                'monster-turno': !turno.esJugador
            }
    },

    },
    computed: {

    }
}
</script>

<style scoped lang="css">
  .src-components-juego {

  }

  .text-center {
    text-align: center;
}

.controls, .log {
    margin-top: 30px;
    text-align: center;
    padding: 10px;
    border: 1px solid #ccc;
    box-shadow: 0px 3px 6px #ccc;
}

.turno {
    margin-top: 20px;
    margin-bottom: 20px;
    font-weight: bold;
    font-size: 22px;
}

.log ul {
    list-style: none;
    font-weight: bold;
    text-transform: uppercase;

}

.log ul li {
    margin: 5px;
    text-align: center;
    padding:5px;

}

.log ul .player-turno {
    color: rgb(39, 97, 131);
    background-color: #b3beff;
}

.log ul .monster-turno {
    text-align: center;
    color:rgb(206, 98, 165);
    background-color:#ffc0c1;
    
}

button {
    font-size: 20px;
    background-color: #c5ccc6;
    padding: 12px;
    box-shadow: 0 1px 1px black;
    margin: 10px;
}

#empezar-partida {
    background-color: #c5ccc6;
}

#empezar-partida:hover {
    background-color: #a5a7a5;
}

#atacar {
    background-color: #c5ccc6;
}

#atacar:hover {
    background-color: #a5a7a5;
}

#ataque-especial {
    background-color: #c5ccc6;
}

#ataque-especial:hover {
    background-color: #a5a7a5;
}

#curar {
    background-color: #c5ccc6;
}

#curar:hover {
    background-color: #a5a7a5;
}

#rendirse {
    background-color: #c5ccc6;
}

#rendirse:hover {
    background-color: #a5a7a5;
}
</style>
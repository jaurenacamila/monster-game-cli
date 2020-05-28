<template>

  <section class="src-components-botones">
    <h1>Botones</h1>
    <section class="row controls" v-if="!hayUnaPartidaEnJuego">
        <div class="small-12 columns">
            <button id="start-game"  @click="empezarPartida">
                EMPEZAR JUEGO NUEVO</button>
        </div>
    </section>
    <section class="row controls" v-else>
        <div class="small-12 columns">
            <button id="atacar" @click="atacar">ATACAR</button>
            <button id="ataque-especial" @click="ataqueEspecial">ATAQUE ESPECIAL</button>
            <button id="curar" @click="curar">CURAR</button>
            <button id="rendirse" @click="terminarPartida">RENDIRSE</button>
        </div>
    </section>

  </section>

</template>

<script lang="js">

  export default  {
    name: 'src-components-botones',
   // props: [],

    props: {
      hayUnaPartidaEnJuego: Boolean,
      empezarPartida: Function,
      atacar: Function,
      ataqueEspecial: Function,
      curar: Function,
      terminarPartida: Function,
    },
    mounted () {

    },
    data () {
      return {

      }
    },
    methods: {
     

    },
    computed: {

    }
}


</script>

<style scoped lang="css">
  .src-components-botones {

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

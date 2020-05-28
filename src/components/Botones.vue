<template>

  <section class="src-components-botones">
    <h1>botones Component</h1>
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
    props: [],
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
</style>

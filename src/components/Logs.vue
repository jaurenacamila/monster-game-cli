<template lang="html">

  <section class="src-components-logs">
    <h1>src-components-logs Component</h1>
     <div class="small-12 columns" >
            <ul>
                <li v-for="(turno,index) in turnos" :key="index"
                :class="cssEvento(turno)"
                :style="{'text-align': turno.esJugador? 'left' : 'right' ,'opacity':index <=1?1:0.5}">
                    {{ turno.text }} 
                </li>
            </ul>
        </div>
  </section>

</template>

<script lang="js">

  export default  {
    name: 'src-components-logs',
    props: [],
    mounted () {

    },
    data () {
      return {
     turnos: [], //es para registrar los eventos de la partida
      }
    },
    methods: {

    },
    computed: {

    }
}


</script>

<style scoped lang="scss">
  .src-components-logs {

  }
</style>

<template>

  <section class="src-components-barra">
    <h1>{{nombreBarra}}</h1>
    
            <h1 class="text-center"><i class="fas fa-grin fa-2x"></i></h1>
            <div class="curarthbar">
                <div class="curarthbar text-center" 
                style="background-color:rgb(39, 97, 131); margin: 0; color: white;" :style="{width: saludJugador + '%'}">
                    {{ getSalud(saludJugador) }} 
                </div>
            </div>
      
  </section>

</template>

<script lang="js">

  export default  {
    name: 'src-components-barra',
    props: ['nombreBarra'],
    mounted () {

    },
    data () {
      return {
        saludJugador: 100,

      }
    },
    methods: {
      getSalud(salud) {
            return `${salud}%`
      },
    },
    computed: {

    }
}


</script>

<style scoped lang="css">
  .src-components-barra {

  }
</style>

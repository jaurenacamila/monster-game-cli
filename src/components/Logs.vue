<template>

  <section class="src-components-logs">
     <div class="small-12 columns" >
            <div>
                <li v-for="(turno,index) in turnos" :key="index"
                :class="cssEvento(turno)"
                :style="{'text-align': turno.esJugador? 'left' : 'right' ,'opacity':index <=1?1:0.5}">
                    {{ turno.text }} 
                </li>
            </div>
        </div>
  </section>

</template>

<script>

  export default  {
    name: 'src-components-logs',
    //props: [],
    props: {
      turnos: Array,
      esJugador: Boolean

    },
    mounted () {

    },
    data () {
      return {
      }
    },
    methods: {
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
  .src-components-logs {


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

.ul {
    font-weight: bold;
    text-transform: uppercase;
    list-style-type: none;
}

.ul li {
    margin: 50px;
    text-align: center;
    padding:5px;
    list-style-type: none;
}

.player-turno {
    padding-left: 10px;
    color: whitesmoke;
    background-color:rgb(206, 138, 50);
  
}

.monster-turno {
    padding-right: 10px;
    color:whitesmoke;
    background-color:rgb(47, 151, 117);
}

</style>

<template>
  <section class="src-components-barra">
    <h1>Barras</h1>
    <h5>{{nombreBarra}}</h5>
             <h1 class="text-center"><i :class="['fas', icono, 'fa-2x']"></i></h1>
            <div class="curarthbar">
                <div class="curarthbar text-center" 
                :style="{'background-color':color , 'margin': 0, 'color': 'white', width: getSalud(salud) + '%'}">
                    {{ getSalud(salud) }} 
                </div>
            </div>
      
  </section>

</template>

<script>

  export default  {
    name: 'src-components-barra',
   // props: ['nombreBarra' , 'color', 'icono', 'salud'],

   props: {
     nombreBarra:String,
     color:String,
     icono:String,
     salud:Number
   },
    mounted () {

    },
    data () {
      return {

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
  h5 {
    color:darkmagenta
  }

  .text-center {
    text-align: center;
}
  .curarthbar {
    width: 80%;
    height: 40px;
    background-color: #eee;
    margin: auto;
    transition: width 500ms;
    font-size: 22px;
}
 
</style>

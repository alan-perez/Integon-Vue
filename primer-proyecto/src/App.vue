<template>
  <div id="app">
      <input type="text" v-model="nombre"/>
    <Hello v-bind:name = "this.nombre" greeting ="what's up?"/>
    Nombre del equipo a consultar: <input type="text" v-model="nombreEquipo"/>
    <InfoEquipo :team="this.nombreEquipo"/>
    
    <br>

  </div>
</template>

<script>
import Hello from './components/Hello'
import InfoEquipo from './components/InfoEquipo'


export default {
  name: 'App',
  data(){
    return{
      nombre:'',
      nombreEquipo:'',
    }
  },
  components: {
    Hello,
    InfoEquipo,
  }
}
</script>


    InfoEquipo<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

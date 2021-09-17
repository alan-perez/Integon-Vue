<template>
  <div>
    <h1>Mostrando info del equipo: {{ team }}</h1>
    <div v-if="this.team.length>0">
      <p>nombre del equipo: {{ this.equipo }}</p>
      <p>nombre corto del equipo: {{ this.nombrecorto }}</p>
      <p>Año de formacion: {{ this.añoFormacion }}</p>
      <p>Deporte: {{ this.deporte }}</p>
      <p>Liga: {{ this.liga }}</p>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
     // result:false,
      equipo: '',
      nombrecorto: '',
      añoFormacion: '',
      deporte: '',
      liga: '',
    }
  },
//   props: ["team"],
props:{
    team:{
        type:String,
        required:true,
    }
},
  methods: {
    async getTeamDetails() {
      return axios
        .get(
          `https://www.thesportsdb.com/api/v1/json/1/searchteams.php?t=${this.team}`).then((response) => {
        console.log(response.data.teams[0]);
        this.equipo = response.data.teams[0].strTeam;
        this.nombrecorto = response.data.teams[0].strTeamShort;
        this.añoFormacion = response.data.teams[0].intFormedYear;
        this.deporte = response.data.teams[0].strSport;
        this.liga = response.data.teams[0].strLeague;

        });
    },
  },
  watch: {
    team: async function (newVal, oldVal) {
      console.log("Prop changed: ", newVal, "| was: ", oldVal);
      await this.getTeamDetails();
    },
  },
};
</script> 

<style>
</style>
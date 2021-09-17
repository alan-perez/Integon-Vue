<template>
  <section class="md:w-1/3 flex flex-col p-12">
  <!-- Profile Card -->
    <h3 class="font-bold font-lg">{{ formData.name }}</h3>
    <p class="mt-2">{{ formData.occupation }}</p>
  </section>
</template>

<script>
import eventBus from '../event-bus'; //importamos al bus de eventos
export default {
  mounted(){
    eventBus.$on('profileUpdate',this.update); //oye eventbus ahi te encargo me avises cuando alguien
                                                //se aviente un profileUpdate
  },
  beforeDestroy(){
    eventBus.$off('profileUpdate',this.update);
  },
  methods:{
    update(formData){
      this.formData = formData;
    }
  },
  data(){
    return{
      formData:{}
    }
  }
  // props: {
  //   formData: {
  //     type: Object,
  //     default() {
  //       return {}
  //     }
  //   }
  // }
}
</script>

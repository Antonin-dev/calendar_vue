<template>
<div :class="className">
  <form class="flex flex-col justify-around h-full ">
    <label for="create" class="text-center underline">Create your task : </label>
    <input type="text" class="rounded-2xl" name="create" id="create" v-model="newAppointment">
    <button v-on:click.prevent="checkForm" class="rounded-2xl bg-green-400" value="valider">Valider</button>
  </form>
</div>
</template>

<script>
export default {
  name: "AddAppointment",
  data(){
    return {
      newAppointment: ""
    };
  },
  methods:{
    checkForm: function () {
      const newAppointmentData = this.newAppointment
      this.newAppointment = "";
      //Envoie de l'event pour recuperer les données
      console.log(newAppointmentData);
      this.$emit("newAppointmentData", newAppointmentData);
    }
  },
  props: [
      "className"
  ]
}

</script>

<style scoped>

</style>

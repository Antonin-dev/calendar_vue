<template>
  <div class="card bg-yellow-200 border-2 rounded-3xl w-1/6 text-center h-32 m-1.5 shadow-2xl relative flex flex-col">
    <h2>{{ date.day }} octobre</h2>
    <div v-if="appointments.length > 0">
<!--      A faire iterer-->
      <Appointment :appointments="appointments"/>
    </div>
    <button v-on:click="toggleModal('')"
            class="bg-green-400 rounded-full text-white w-8 h-8 absolute bottom-1.5 right-1.5">+
    </button>
  </div>
  <AddAppointment @newAppointmentData="newAppointmentFunc" :className="className"/>
</template>

<script>
import Appointment from "./Appointment.vue";
import AddAppointment from "./AddAppointment.vue";

export default {
  name: "Card",
  components: {AddAppointment, Appointment},
  props: [
    "date"
  ],
  data() {
    return {
      appointments: [],
      className: "hidden"
    }
  },
  methods: {
    toggleModal(value) {
      this.className = value;
    },
    newAppointmentFunc: function (newAppointment) {
      this.appointments = [...this.appointments, newAppointment];
      this.toggleModal("hidden");
    }
  }
}
</script>

<style scoped>
button {
  transition: all .2s ease-in-out;
}

button:hover {
  transform: scale(1.2);
}
</style>

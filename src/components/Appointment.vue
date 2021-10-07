<template>
  <div v-for="appointment in appointments" class="flex justify-center items-center">
    <p key="appointment"  :class="classNameText">{{ appointment }}</p>
    <div v-on:click="lineThrough" :class="classNameDelete">x</div>
  </div>
</template>

<script>
export default {
  name: "Appointment",
  props: [
    "appointments"
  ],
  data() {
    return {
      isClose: false,
      classNameText: "",
      classNameDelete : "bg-red-500 w-4 h-4 rounded-full text-xs text-white ml-2 cursor-pointer delete"
    };
  },
  methods: {
    lineThrough() {
      this.isClose = !this.isClose;
      if (this.isClose === true) {
        this.classNameText = "line-through text-red-800";
        this.classNameDelete = "hidden"
      }
    }
  }
}
</script>

<style scoped>
.delete { transition: all .2s ease-in-out; }
.delete:hover { transform: scale(1.2); }
</style>

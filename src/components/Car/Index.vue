<template>
    <div>
      <h1>Get All Cars</h1>
      <div>จํานวนรถ {{ Cars.length }}</div>
      <div v-for="user in users" v-bind:key="Car.id">
        <div>category: {{ Car.category }}</div>
        <div>engine_capacity: {{ Car.engine_capacity }} </div>
        <div>model: {{ Car.model }}</div>
        <div>brand: {{ Car.brand }}</div>
        <div>color: {{ Car.color }}</div>
        <div>lc_plate: {{ Car.lc_plate }}</div>
        <div>chasis_no: {{ Car.chasis_no }}</div>
        <p>
          <button v-on:click="navigateTo('/car/' + Car.id)">
            ดูข้อมูลรถ
          </button>
          <button v-on:click="navigateTo('/car/edit/' + Car.id)">
            แกไขข้อมูล
          </button>
          <button v-on:click="deleteUser(Car)">ลบข้อมูล</button>
        </p>
        <hr />
      </div>
    </div>
  </template>
  <script>
  import CarsService from "@/services/CarsService";
  export default {
    data() {
      return {
        Cars: []
      };
    },
    methods: {
      navigateTo(route) {
        this.$router.push(route);
      },
      async deleteUser(Car) {
        let result = confirm("Want to delete?");
        if (result) {
          try {
            await CarServices.delete(car);
            this.refreshData()
          } catch (err) {
            console.log(err);
          }
        }
      },
      async refreshData() {
        this.Cars = (await CarServices.index()).data;
      }
    },
    async created() {
      this.Cars = (await CarServices.index()).data;
    }
  };
  </script>
  <style scoped></style>
  
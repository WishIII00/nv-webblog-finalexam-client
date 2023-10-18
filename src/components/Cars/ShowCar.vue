<template>
    <div>
      <h1>Show Car</h1>
      <div>category: {{ car.category }}</div>
        <div>engine_capacity: {{ car.engine_capacity }} </div>
        <div>model: {{ car.model }}</div>
        <div>brand: {{ car.brand }}</div>
        <div>color: {{ car.color }}</div>
        <div>lc_plate: {{ car.lc_plate }}</div>
        <div>chasis_no: {{ car.chasis_no }}</div>
    </div>
  </template>
  <script>

  import CarsService from "@/services/CarsService";
  
  export default {
    data() {
      return {
        car: null
      };
    },
    async created() {
      let carId = this.$route.params.carId;
      this.Car = (await CarsService.show(carId)).data
      console.log(this.CarId)
    }
  };
  </script>
  <style scoped></style>
  
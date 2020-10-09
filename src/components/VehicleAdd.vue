<template>
  <div class="col-4">
    <form @submit.prevent="submitForm">
      <div class="form-group card p-3">
        <div class="card-header mb-2">Vehicle Details</div>
        <div class="form-group">
          <label class="float-left" for="name">Name</label>
          <input
            type="text"
            class="form-control"
            v-model="name"
            placeholder="Name"
          />
        </div>
        <div class="form-group">
          <label class="float-left" for="engine_displacement"
            >Engine Displacement</label
          >
          <input
            type="number"
            class="form-control"
            v-model="engine_displacement"
            placeholder="Engine Displacement"
          />
        </div>
        <div class="form-group">
          <label class="float-left" for="engine_power">Engine power</label>
          <input
            type="text"
            class="form-control"
            v-model="engine_power"
            placeholder="Engine Power"
          />
        </div>
        <div class="form-group">
          <label class="float-left" for="price">Price</label>
          <input
            type="text"
            class="form-control"
            v-model="price"
            placeholder="Price"
          />
        </div>
        <div class="form-group">
          <label class="float-left" for="location">Location</label>
          <input
            type="text"
            class="form-control"
            v-model="location"
            placeholder="Location"
          />
        </div>

        <button type="submit" class="btn btn-primary float-left">Submit</button>
      </div>
    </form>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "VehicleAdd",
  data() {
    return {
      vehicles: [],
      name: "",
      engine_displacement: "",
      engine_power: "",
      price: "",
      location: "",
    };
  },
  methods: {
    submitForm() {
      axios
        .post("http://localhost:8000/vehicle", {
          name: this.name,
          engine_displacement: this.engine_displacement,
          engine_power: this.engine_power,
          price: this.price,
          location: this.location,
        })
        .then((response) => {
          console.log(response);
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
};
</script>

<style scoped>
</style>
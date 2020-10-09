<template>
  <div class="row">
    <div class="col-8 float-left">
      <table class="table">
        <thead>
          <tr>
            <th scope="col">#</th>
            <th scope="col">Name</th>
            <th scope="col">Engine Displacement</th>
            <th scope="col">Engine Power</th>
            <th scope="col">Price</th>
            <th scope="col">Location</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="itemVehicle in vehicles" v-bind:key="itemVehicle.id">
            <th scope="row">{{ itemVehicle.id }}</th>
            <td>{{ itemVehicle.name }}</td>
            <td v-if="itemVehicle.engine_displacement < 50">
              {{ itemVehicle.engine_displacement }} L
            </td>
            <td v-else>{{ itemVehicle.engine_displacement }} CC</td>
            <td>{{ itemVehicle.engine_power }} HP</td>
            <td>${{ itemVehicle.price }}</td>
            <td>{{ itemVehicle.location }}</td>
          </tr>
        </tbody>
      </table>
    </div>
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
              type="text"
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

          <button type="submit" class="btn btn-primary float-left">
            Submit
          </button>
        </div>
      </form>
    </div>
    *Note: Customer just need to input what they know about their vehicle engine
    displacement, either its in x,x L or xxxx CC.
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "VehicleList",
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
  mounted() {
    this.load();
  },
  methods: {
    load() {
      axios
        .get("http://localhost:8000/vehicle")
        .then((res) => (this.vehicles = res.data))
        .catch((err) => console.log(err));
    },
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
          this.load();
          console.log(response);
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
};
</script>
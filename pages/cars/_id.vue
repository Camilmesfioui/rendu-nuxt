<template>
  <div class="container">
    <h1>{{ currentCar.brand }}</h1>
    <p>
      {{ currentCar.model }}
    </p>
    <button v-on:click="deleteCar">Delete</button>
    <nuxt-link :to="{name: 'cars'}">
      <button>Back</button>
    </nuxt-link>
  </div>
</template>

<script>
  import axios from "~/plugins/axios";

  export default {
    methods: {

      async deleteCar() {
        // const response = await axios.delete(`/cars/${this.currentCar.id}`);

        axios.delete(`/cars/${this.currentCar.id}`).then(function(){
          window.location.replace("http://localhost:3000/cars")
        });
      }
    },

    async asyncData({ params }) {
      const { data } = await axios.get(`/cars/${params.id}`);

      return {
        currentCar: data
      }
    },

    data() {
      return {
        currentCar: null
      }
    },

    head() {
      return {
        title: `${this.currentCar.brand} | Mon site internet`,
        meta: [
          {}
        ]
      }
    }
  }
</script>

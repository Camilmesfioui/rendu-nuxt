<template>
  <div class="container">
    <h1>{{ currentCar.brand }}</h1>
    <p>
      {{ currentCar.model }}
    </p>
    <nuxt-link :to="{name: 'cars'}">
      <button>Retour</button>
    </nuxt-link>
  </div>
</template>

<script>
  import axios from "~/plugins/axios";

  export default {
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

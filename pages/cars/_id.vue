<template>
  <div class="container">
    <h1>{{ currentCar.brand }}</h1>
    <p>
      {{ currentCar.model }}
    </p>
    <input v-model="brand" type="text" placeholder="brand">
    <input v-model="model" type="text" placeholder="model">
    <button v-on:click="edit">Modify</button>
    <nuxt-link :to="{name: 'cars'}">
      <button>Retour</button>
    </nuxt-link>
  </div>
</template>

<script>
  import axios from "~/plugins/axios";

  export default {
    methods: {
      edit: function () {
        axios.put(`/cars/${this.currentCar.id}`, {
          brand: this.brand,
          model: this.model
        })
        .then(function(response){
          location.reload();
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

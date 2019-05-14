<template>
  <div class="container">
    <h2>{{ title }}</h2>
    <ul>
      <li v-for="car in cars" :key="car.id">
        <nuxt-link :to="{name: 'cars-id', params: {id: car.id}}">
          {{ car.brand }}
        </nuxt-link>
      </li>
    </ul>
    <input v-model="brand" type="text" placeholder="brand">
    <input v-model="model" type="text" placeholder="model">
    <button v-on:click="insert">Create Car</button>
  </div>
</template>

<script>
  import axios from "~/plugins/axios";

  export default {
    methods: {
      insert: function () {
        axios.post('/cars', { brand: this.brand , model: this.model })
          .then(function(response){
            location.reload();
          });
      }
    },

    async asyncData() {

      const { data } = await axios.get('/cars');

      return {
        cars: data
      }

    },
    data() {
      return {
        title: "Cars",
        cars: [],
        brand: null,
        model: null
      }
    }
  }
</script>

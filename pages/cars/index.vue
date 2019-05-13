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
  </div>
</template>

<script>
  import axios from "~/plugins/axios";

  export default {
    async asyncData() {
      const { data } = await axios.get('/cars');

      return {
        cars: data
      }
    },
    data() {
      return {
        title: "Cars",
        cars: []
      }
    }
  }
</script>

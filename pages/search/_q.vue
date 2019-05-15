<template>
  <div class="container">
    <h5 class="card-title">{{ title }}</h5>

    <div class="card-group">
      <div class="row">
        <car  v-for="car in cars" :car="car"></car>
      </div>
    </div>

  </div>
</template>
<script>
  import axios from "~/plugins/axios";

  import Car from '~/components/Car.vue';

  export default {
    components: {
      Car
    },

    async asyncData({params}) {
      const {data} = await axios.get(`/cars?q=${params.q}`);

      return {
        cars: data
      }
    },

    data() {
      return {
        title: "Search result",
        cars: []
      }
    }
  }
</script>

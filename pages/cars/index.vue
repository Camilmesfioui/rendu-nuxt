<template>
  <div class="container">
      <h1>{{ title }}</h1>

      <!-- Button trigger modal -->
      <button type="submit" class="btn btn-primary create" data-toggle="modal" data-target="#exampleModalCenter">
        Créer une voiture
      </button>

      <!-- Modal -->
      <div class="modal fade" id="exampleModalCenter" tabindex="-1" role="dialog" aria-labelledby="exampleModalCenterTitle" aria-hidden="true">
        <div class="modal-dialog modal-dialog-centered" role="document">
          <div class="modal-content">
            <input v-model="brand" type="text" placeholder="brand" class="form-control">
            <input v-model="model" type="text" placeholder="model" class="form-control">
            <input v-model="imgLink" type="text" placeholder="img link" class="form-control">
            <textarea v-model="detail" placeholder="detail" class="form-control"></textarea>
            <button v-on:click="insert" class="btn btn-primary" data-dismiss="modal">Create Car</button>
          </div>
        </div>
      </div>

      <div class="card-group">
        <div class="row">
          <car  v-for="car in cars" :car="car"></car>
        </div>
      </div>

  </div>
</template>

<style>
  img {
    width: 100%;
    padding: 20px;
  }
  .btn {
    margin: 5px;
  }
  .modal-content {
    padding: 20px;
  }
  .card {
    margin-bottom: 10px;
  }
  .create{
    display: block;
    margin: 10px auto;
  }
</style>

<script>
  import axios from "~/plugins/axios";
  import Car from '~/components/Car.vue';

  export default {
    components: {
      Car
    },

    methods: {
      async insert () {
        const car = {
          brand: this.brand,
          model: this.model,
          detail: this.detail,
          imgLink: this.imgLink
        };

        await axios.post('/cars', car);

        this.cars = await this.getCars();

      },

      async getCars() {
        const { data } = await axios.get('/cars');
        return data;
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
        title: "My Car List",
        cars: [],
        brand: null,
        model: null,
        detail: null,
        imgLink: null
      }
    },

  }
</script>

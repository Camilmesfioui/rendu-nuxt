<template>
  <div class="container">
    <img class="card-img-top" src="data:image/jpeg;base64,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" alt="Card image cap">

    <h1>{{ currentCar.brand }}</h1>
    <p>
      {{ currentCar.model }}
    </p>

    <!-- Button trigger modal -->
    <button type="button" class="btn btn-primary" data-toggle="modal" data-target="#exampleModalCenter">
      Options
    </button>
    <nuxt-link :to="{name: 'cars'}">
      <button class="btn btn-success">Back</button>
    </nuxt-link>

    <!-- Modal -->
    <div class="modal fade" id="exampleModalCenter" tabindex="-1" role="dialog" aria-labelledby="exampleModalCenterTitle" aria-hidden="true">
      <div class="modal-dialog modal-dialog-centered" role="document">
        <div class="modal-content">
          <input v-model="brand" type="text" placeholder="brand" class="form-control">
          <input v-model="model" type="text" placeholder="model" class="form-control">

          <button v-on:click="edit" class="btn btn-warning">Edit car infos</button>
          <button v-on:click="deleteCar" class="btn btn-danger" data-dismiss="modal">Delete car</button>
        </div>
      </div>
    </div>

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
          .then(function () {
            location.reload();
          });
      },

      async deleteCar() {
        await axios.delete(`/cars/${this.currentCar.id}`);
        this.$router.push({name: 'cars'});
      },
    },

    async asyncData({params}) {
      const {data} = await axios.get(`/cars/${params.id}`);

      return {
        brand: data.brand,
        model: data.model,
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
        title: `${this.currentCar.brand} | Cars`,
        meta: [
          {}
        ]
      }
    }
  }
</script>

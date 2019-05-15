<template>
  <div class="container">
    <img class="card-img-top" :src="currentCar.imgLink" alt="Card image cap">

    <h1>{{ currentCar.brand }}, {{ currentCar.model }}</h1>
    <p>
      {{ currentCar.detail }}
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
          <input v-model="imgLink" type="text" placeholder="img link" class="form-control">
          <textarea v-model="detail" placeholder="detail" class="form-control"></textarea>
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
          model: this.model,
          detail: this.detail,
          imgLink: this.imgLink
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
        detail: data.detail,
        imgLink: data.imgLink,
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

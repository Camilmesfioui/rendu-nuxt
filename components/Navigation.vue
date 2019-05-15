<template>
  <nav class="navbar navbar-expand-lg navbar-light bg-light">
    <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent"
            aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>

    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <ul class="navbar-nav mr-auto">
        <li class="nav-item active">
          <a class="nav-link" href="/">Home <span class="sr-only">(current)</span></a>
        </li>
        <li class="nav-item">
          <nuxt-link class="nav-link" :to="{name: 'cars'}">
            Cars
          </nuxt-link>
        </li>
      </ul>
      <div class="form-inline my-2 my-lg-0">
        <input v-model="q" class="form-control mr-sm-2" type="search" placeholder="Search" aria-label="Search">
        <button @click="search" class="btn btn-outline-success my-2 my-sm-0">Search</button>
      </div>
    </div>
  </nav>
</template>

<script>
  export default {
    data() {
      return {
        q: null,
      }
    },
    methods: {
      search() {
        if (this.q) {
          this.$router.push({name: 'search-q', params: {q: this.q}})
        }
      }
    }
  }
</script>


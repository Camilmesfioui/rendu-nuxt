<template>
    <div class="card col-4 col-md-4 col-sm-4 col-xs-4">
        <img class="card-img-top" :src="car.imgLink" alt="Card image cap">
        <div class="card-body">
            <h5 class="card-title">{{ car.brand }}</h5>
            <p class="card-text">{{ car.detail }}</p>
        </div>
        <nuxt-link :to="{name: 'cars-id', params: {id: car.id}}">
            <button class="btn btn-primary">Check out</button>
        </nuxt-link>
    </div>
</template>

<script>
    export default {
        props: ['car'],
    }
</script>

<template>
  <div class="container mx-auto px-6 py-2">
    <h3 class="text-gray-600 text-center p-2">Cars GraphQL APP</h3>
    <div v-for="car in allCars" :key="car.id">
      <h2>{{ car.make }} - {{ car.model }}</h2>
      <p class="text-blue-500 underline mb-2">
        <NuxtLink :to="`car/${car.id}`">Details</NuxtLink>
      </p>
    </div>
  </div>
</template>

<script>
import allCars from '~/apollo/queries/allCars'
export default {
  components: {},
  apollo: {
    allCars: {
      prefetch: true,
      query: allCars
    }
  },
  head: {
    title: 'Cars with Apollo'
  },
  created() {
    console.log('server:', process.server, 'allCars:', this.allCars)
  }
}
</script>

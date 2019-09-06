<template>
  <div class="container mx-auto p-4">
    <div v-if="Car">
      <div class="flex justify-between p-2">
        <h3 class="text-gray-700">{{ Car.make }} {{ Car.model }}</h3>
        <p class="text-blue-600">{{ formatCurrency(Car.price) }}</p>
      </div>
      <img :src="Car.photoURL" :alt="`${Car.model} photo`" />
      <p class="text-yellow-600 p-4">
        <NuxtLink to="/">
          Home page
        </NuxtLink>
      </p>
    </div>
  </div>
</template>

<script>
import car from '~/apollo/queries/car'
export default {
  apollo: {
    Car: {
      query: car,
      prefetch: ({ route }) => ({ id: route.params.id }),
      variables() {
        return { id: this.$route.params.id }
      }
    }
  },
  methods: {
    formatCurrency(num) {
      const formatter = new Intl.NumberFormat('en-US', {
        style: 'currency',
        currency: 'USD',
        minimumFractionDigits: 2
      })
      return formatter.format(num)
    }
  },
  head() {
    return {
      title: this.Car ? `${this.Car.make} ${this.Car.model}` : 'Loading'
    }
  }
}
</script>

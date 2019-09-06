<template>
  <div>
    <ct-header></ct-header>
    <div class="container mx-auto mt-4">
      <nuxt />
    </div>
  </div>
</template>

<script>
import CtHeader from '@/components/CtHeader'
export default {
  components: {
    CtHeader
  }
}
</script>

<template>
  <div>
    <!-- {{ $route.params.species }}{{ $route.params.id }} -->
    <!-- {{ cats[$route.params.id] }}
    {{ [$route.params.species][$route.params.id].name }} -->
    <!-- {{ this.pet($route.params.species)[$route.params.id].name }}  -->

    <h1>{{ `${animal.name} (${$route.params.species})` }}</h1>
    <p>age: {{ animal.age }}</p>
    <p>breed: {{ animal.breed }}</p>
    <p>weight: {{ animal.weight }}</p>
  </div>
</template>

<script>
import { mapState } from 'vuex'

export default {
  data() {
    return {
      animal: {}
    }
  },
  computed: {
    ...mapState(['cats', 'dogs'])
  },
  mounted() {
    this.animal = this[this.$route.params.species][this.$route.params.id]
  }
}
</script>

<template>
  <div class="home">
<calculator-app />
  </div>
</template>

<script>
// @ is an alias to /src
import calculatorApp from '@/components/calculatorApp.vue'

export default {
  name: 'HomeView',
  components: {
    calculatorApp
  }
}
</script>

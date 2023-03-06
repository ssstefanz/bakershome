<template>
  <div class="app">
    <main class="main">
      <div class="grid">
        <!-- baker's timer -->
        <Timer></Timer>

        <!-- recipe card -->
        <div class="grid__card">
          <TodayRecipe></TodayRecipe>
        </div>
          
        <!-- baker's calculator -->
        <Calculator></Calculator>
      </div>
    </main>
  </div>
</template>

<script>
import Calculator from '@/components/calculator.vue'
import Timer from '@/components/timer.vue'
import TodayRecipe from '@/components/TodayRecipe.vue'

    export default {
    name: 'app',
    components: [
      Calculator,
      Timer,
      TodayRecipe
    ]
    
}
</script>
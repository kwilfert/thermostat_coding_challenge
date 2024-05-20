<script setup>
// Props: maximumg, minimum and current temperature
defineProps(
    {
      maxTemperature: {
        type: Number,
        required: true
      },
      minTemperature: {
        type: Number,
        required: true
      },
      currentTemperature: {
        type: Number,
        required: true
      }
    }
)
</script>
<template>
  <div>
    <!-- thermostat -->
  </div>
</template>

<style scoped>

</style>
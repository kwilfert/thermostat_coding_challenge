<script setup>
// Props: maximumg, minimum and current temperature
// Import SVG files as raw text
import scale_svg_raw from '../assets/images/thermostat_scale.svg?raw';
import indicator_svg_raw from '@/assets/images/thermostat_indicator.svg?raw';

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
  <div class="thermostat-display">
    <div class="scale" v-html="scale_svg_raw"></div>
    <div class="indicator" v-html="indicator_svg_raw"></div>
  </div>
</template>

<style scoped>
.thermostat-display {
  position: relative;
  width: 200px;
  height: 200px;
  text-align: center;
}

.scale,
.indicator {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}
</style>
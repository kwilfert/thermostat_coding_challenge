<script lang="ts" setup>
// Import necessary functions and raw SVGs
import {computed} from 'vue';
import scale_svg_raw from '@/assets/images/thermostat_scale.svg?raw';
import indicator_svg_raw from '@/assets/images/thermostat_indicator.svg?raw';

// Define props for the component
const props = defineProps({
  maxTemperature: {
    type: Number,
    required: true,
  },
  minTemperature: {
    type: Number,
    required: true,
  },
  currentTemperature: {
    type: Number,
    required: true,
  },
});

// Calculate the indicator angle
const indicatorAngle = computed(() => {
  const {currentTemperature, minTemperature, maxTemperature} = props;
  const percentage = (currentTemperature - minTemperature) / (maxTemperature - minTemperature);
  return percentage * 180 - 90; // Convert to degrees (-90 to 90)
});

// Set the indicator style
const indicatorStyle = computed(() => {
  return {
    transform: `rotate(${indicatorAngle.value}deg)`,
    transformOrigin: 'center center',
  };
});
</script>

<template>
  <div class="thermostat-display">
    <div class="temperature-display">{{ props.currentTemperature }}°</div>
    <div class="scale" v-html="scale_svg_raw"></div>
    <div :style="indicatorStyle" class="indicator" v-html="indicator_svg_raw"></div>
    <div class="min-temperature">{{ props.minTemperature }}°</div>
    <div class="max-temperature">{{ props.maxTemperature }}°</div>
  </div>
</template>

<style scoped>
.thermostat-display {
  position: relative;
  width: 200px;
  height: 200px;
  text-align: center;
  margin: 0 auto;
  background-color: #f9f9f9;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  padding: 20px;
}

.scale,
.indicator {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

.temperature-display {
  text-align: center;
  position: absolute;
  top: 65px;
  left: 50%;
  transform: translateX(-50%);
  font-size: 24px;
  font-weight: bold;
  border-radius: 5px;
  padding: 5px 10px;
}

.min-temperature {
  position: absolute;
  top: 100px;
  left: 10px;
  font-size: 14px;
  transform: translateY(50%);
  font-weight: bold;
  color: #007bff;
}

.max-temperature {
  position: absolute;
  top: 100px;
  right: 10px;
  font-size: 14px;
  transform: translateY(50%);
  font-weight: bold;
  color: #ff0000;
}
</style>

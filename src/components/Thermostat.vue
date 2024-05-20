<script setup>
// Props: maximumg, minimum and current temperature
// Import SVG files as raw text
import scale_svg_raw from '../assets/images/thermostat_scale.svg?raw';
import indicator_svg_raw from '@/assets/images/thermostat_indicator.svg?raw';
import {computed} from "vue";

// define relevant input values for thermostat component
const props = defineProps(
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

// calculate indicator angle
const indicatorAngle = computed(() => {
  const {currentTemperature, minTemperature, maxTemperature} = props;
  const percentage = (currentTemperature - minTemperature) / (maxTemperature - minTemperature);
  return percentage * 180 - 90; // Convert to degrees (-90 to 90)
});

// set indicator style
const indicatorStyle = computed(() => {
  return {
    transform: `rotate(${indicatorAngle.value}deg)`,
    transformOrigin: 'center center',
  };
});


</script>
<template>
  <div class="thermostat-display">
    <div class="temperature-display">{{ currentTemperature }}°</div>
    <div class="scale" v-html="scale_svg_raw"></div>
    <div :style="indicatorStyle" class="indicator" v-html="indicator_svg_raw"></div>
    <div class="min-temperature">{{ minTemperature }}°</div>
    <div class="max-temperature">{{ maxTemperature }}°</div>
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

.min-temperature {
  position: absolute;
  bottom: 10px;
  left: 10px;
  font-size: 12px;
}

.max-temperature {
  position: absolute;
  bottom: 10px;
  right: 10px;
  font-size: 12px;
}
</style>
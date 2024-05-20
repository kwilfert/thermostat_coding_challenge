<script setup>
import HelloWorld from './components/HelloWorld.vue'
import Thermostat from "@/components/Thermostat.vue";
import {ref} from "vue";

const minTemperature = ref(0);
const maxTemperature = ref(0);
const currentTemperature = ref(0);
</script>

<template>
  <header>
    <img alt="Thermometer App Logo" class="logo" height="125" src="./assets/thermostat_logo.png" width="125"/>
    <div class="wrapper">
      <HelloWorld msg="Thermostat Coding Exercise"/>
    </div>
  </header>

  <main>
    <h1>Thermostat Demonstration</h1>
    <div>
      <!-- temperature control inputs -->
      <label for="minTemperature">Min. Temperature</label><br>
      <input id="minTemperature" v-model="minTemperature" type="number"><br>
      <label for="maxTemperature">Max. Temperature</label><br>
      <input id="maxTemperature" v-model="maxTemperature" type="number"><br>
      <label for="currentTemperature">Current Temperature</label><br>
      <input id="currentTemperature" v-model="currentTemperature" type="number"><br>
    </div>
    <!-- Thermostat for display of values-->
    <Thermostat :currentTemperature="currentTemperature"
                :maxTemperature="maxTemperature"
                :minTemperature="minTemperature"/>
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>

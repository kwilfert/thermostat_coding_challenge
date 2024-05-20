<script setup>
import HelloWorld from './components/HelloWorld.vue'
import Thermostat from "@/components/Thermostat.vue";
import thermostat_logo from "@/assets/images/thermostat_logo.png";
import {ref} from "vue";

const minTemperature = ref(20);
const maxTemperature = ref(35);
const currentTemperature = ref(25);
</script>

<template>
  <header>
    <img :src="thermostat_logo" alt="Thermometer App Logo" class="logo" height="125" width="125"/>
    <div class="wrapper">
      <HelloWorld msg="Thermostat Coding Exercise"/>
    </div>
  </header>

  <main>
    <h1>Thermostat Demonstration</h1>
    <div class="inputs">
      <!-- temperature control inputs -->
      <label for="minTemperature">Min. Temperature</label>
      <input id="minTemperature" v-model="minTemperature" type="number">
      <label for="maxTemperature">Max. Temperature</label>
      <input id="maxTemperature" v-model="maxTemperature" type="number">
      <label for="currentTemperature">Current Temperature</label>
      <input id="currentTemperature" v-model="currentTemperature" type="number">
    </div>
    <div class="thermostat">
      <!-- Thermostat for display of values-->
      <Thermostat :currentTemperature="currentTemperature"
                  :maxTemperature="maxTemperature"
                  :minTemperature="minTemperature"/>
    </div>
  </main>
</template>

<style scoped>
.inputs {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  max-width: 300px;
  margin: 1rem auto;
  padding: 1rem;
  border-radius: 8px;
  background-color: #f9f9f9;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}
.inputs label {
  font-weight: bold;
  margin-bottom: 0.5rem;
}

.inputs input {
  padding: 0.5rem;
  border: 1px solid #ccc;
  border-radius: 4px;
}

header {
  text-align: center;
  line-height: 1.5;
  padding: 1rem 0;
  background-color: #fafafa;
  border-bottom: 1px solid #ddd;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

h1 {
  text-align: center;
  margin: 2rem 0;
}

.thermostat {
  display: flex;
  justify-content: center;
  margin: 2rem 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    align-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>

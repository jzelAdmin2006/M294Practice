<script setup>
import { ref } from 'vue'
import { computed } from 'vue'
const temperatureCelsius = ref(0)
const temperatureFahrenheit = computed(() => temperatureCelsius.value * 1.8 + 32)
const temperatureKelvin = computed(() => temperatureCelsius.value + 273.15)
const isFreezing = computed(() => temperatureCelsius.value < 0)

function colder() {
  temperatureCelsius.value--
}

function warmer() {
  temperatureCelsius.value++
}
</script>

<template>
  <body>
    <h1>Wetterstation</h1>
    <div class="table">
    <th>
      <p>Temperatur in Celsius</p>
      <p>Temperatur in Fahrenheit</p>
      <p>Temperatur in Kelvin</p>
      <p>Gefrierpunkt unterschritten</p>
    </th>
    <td>
      <p>{{ temperatureCelsius }}°C</p>
      <p>{{ temperatureFahrenheit }}°F</p>
      <p>{{ temperatureKelvin }}°K</p>
      <p v-if="isFreezing">Ja</p><p v-else>Nein</p>
    </td>
    </div>
    <button @click="colder">Es wird kälter</button>
    <button @click="warmer">Es wird wärmer</button>
  </body>
</template>

<style>
  body {
    text-align: center;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  }
  .table {
    display: table;
    width: 300px;
    margin: 20px auto;
  }
  .table th {
    text-align: left;
  }
  .table td {
    text-align: right;
  }
  button + button {
    margin-left: 20px;
  }
</style>
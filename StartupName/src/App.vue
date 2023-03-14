<script setup>
import { ref } from 'vue'

const prefixes = [
  'Hype',
  'Biz',
  'Lolz',
  'Rofl',
  'Galaxy',
  'Biz',
  'Fan',
  'Buzz',
  'Real',
  'Solid',
  'Inter',
  'Active',
  'Swoosh',
]

const suffixes = [
  'park',
  'span',
  'cloud',
  'loop',
  'verse',
  'layer',
  'er',
  'r',
  'dot',
  'dock',
  'space',
  'yard',
  'scale',
  'signal',
  'press',
  'ware',
  'port',
]
  
const name = ref('???')

function generate() {
  name.value = getRandomName()
}
  
function getRandomName() {
  return prefixes[Math.floor(Math.random()*prefixes.length)] + suffixes[Math.floor(Math.random()*suffixes.length)]
}
</script>

<template>
  <div>
    <h1>Dein Startup heisst</h1>
    <p>
      {{name}}
    </p>
    <button @click="generate">
      Namen generieren
    </button>
  </div>
</template>

<style>
  div {
    text-align:center;
    font-family: 'Helvetica Neue', Helvetica, Arial, sans-serif;
  }
  
  p {
    border: 1px solid #dcdcdc;
    border-radius: 10px;
    padding: 10px;
    background-color: #f5f5f5;
	}
</style>
<script setup>
import { ref } from 'vue'
import HelloWorld from './HelloWorld.vue'
</script>

<template>
  <p>Wichtig: Doppelpunkt vor showText property, sonst wird true als String und nicht typenlos interpretiert.</p>
  <HelloWorld msg="Hello World!" :showText="true" />
</template>

<style></style>
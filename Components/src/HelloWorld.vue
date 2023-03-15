<script setup>
defineProps({
    msg: { type: String, required: true },
    showText: { type: Boolean, required: false }
})
</script>

<template>
    <h1 v-if="showText">{{ msg }}</h1>
</template>
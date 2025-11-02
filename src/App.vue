<template>
  <div class="min-h-screen bg-slate-50 p-6">
    <h1 class="mb-6 text-2xl font-bold">Distintos botones</h1>
    <div class="flex gap-3">
      <BaseButton v-on:click="count++"># de clicks: {{ count }}</BaseButton>
      <BaseButton variant="danger" v-on:click="count = 0">Borrar</BaseButton>
      <BaseButton :disabled="true" variant="secondary">No funciona</BaseButton>
      <BaseButton variant="extra">Btn extra</BaseButton>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue"
import BaseButton from "./components/BaseButton.vue"
const count = ref(0)
</script>

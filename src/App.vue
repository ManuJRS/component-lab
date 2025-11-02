<template>
  <main class="min-h-screen bg-slate-100 p-10 space-y-10">
    <!--Aquiestan los btns-->
    <section class="rounded-2xl bg-white p-6 shadow-sm">
      <h2 class="mb-4 text-xl font-semibold text-slate-800 pb-2">Distintos botones</h2>
      <div class="flex flex-wrap gap-3">
        <BaseButton @click="count++"># de clicks: {{ count }}</BaseButton>
        <BaseButton variant="danger" @click="count = 0">Borrar</BaseButton>
        <BaseButton disabled variant="secondary">No funciona</BaseButton>
        <BaseButton variant="extra">Btn extra</BaseButton>
      </div>
    </section>
    <!--aquiestan los inputs-->
    <section class="rounded-2xl bg-white p-6 shadow-sm">
      <h2 class="mb-4 text-xl font-semibold text-slate-800 pb-2">Distintos inputs</h2>

      <div class="space-y-6 max-w-md">
        <BaseInput
          v-model="name"
          label="Nombre"
          placeholder="Escribe tu nombre aqui"
          :helperText="nameError ? 'No puede estar vacío ni contener números' : 'Este campo es mandatory'"
          :error="nameError"
          variant="default"
          size="md"
        />

        <BaseInput
          v-model="email"
          label="Tu correo"
          type="email"
          placeholder="tucorreo@ejemplo.com"
          helperText="Usa un email válido"
          variant="default"
          size="sm"
        />

        <BaseInput
          v-model="password"
          label="Contraseña"
          type="password"
          placeholder="••••••••"
          helperText="Debe tener mínimo 8 caracteres"
          :error="password.length > 0 && password.length < 8"
          variant="default"
          size="lg"
        />
      </div>
    </section>
  </main>
</template>

<script setup>
import { ref, computed} from "vue"
import BaseButton from "./components/BaseButton.vue"
import BaseInput from "./components/BaseInput.vue";
const count = ref(0)
const name = ref('')
const email = ref('')
const password = ref('')

const nameError = computed(function() {
  const valueWithoutSpaces  = name.value.trim()
  return valueWithoutSpaces.length === 0 || /\d/.test(valueWithoutSpaces)
})
</script>

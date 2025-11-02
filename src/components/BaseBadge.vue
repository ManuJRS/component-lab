<template>
    <span
    v-bind:class="classes"
    class="mr-2 ml-2"
    >
    <slot/>
    </span>
</template>

<script setup>
    import { computed } from 'vue';
    const props = defineProps({
        variant: {
            type: String,
            default: 'gray'
        }
    })

    const classes = computed(function(){
        const base = 'inline-flex items-center rounded-full px-2.5 py-0.5 text-xs font-medium'
        const variants = {
            gray: 'bg-slate-100 text-slate-700 ring-1 ring-inset ring-slate-200',
            blue: 'bg-blue-100 text-blue-700 ring-1 ring-inset ring-blue-200',
            green: 'bg-green-100 text-green-700 ring-1 ring-inset ring-green-200',
            red: 'bg-red-100 text-red-700 ring-1 ring-inset ring-red-200'
        }
        const chose = variants[props.variant] || variants.gray
        return `${base} ${chose}`
    })
</script>
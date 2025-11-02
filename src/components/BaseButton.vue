<template>
    <button
    v-bind:type="btnStyle"
    v-bind:disabled="disabled"
    v-bind:class="[classes, $attrs.class]"
    v-on:click="$emit('btn-click')"
    class="inline-flex items-center justify-center rounded-xl px-4 py-2 font-medium bg-blue-600 text-white
    transition hover:brightness-110 active:scale[.98] 
    focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-blue-500 cursor-pointer">
        <slot/>
    </button>
</template>

<script setup>
import { computed } from 'vue';

const props = defineProps({
    btnStyle: {
        type: String,
        default: "button"
    },
    disabled: {
        type: {
            type: Boolean,
            default: false
        }
    },
    variant: {
        type: String,
        default: "primary"
    }
})

const classes = computed(function () {
    const base = "inline-flex items-center justify-center rounded-xl px-4 py-2 font-medium transition active:scale-[.98]"
    const focus = "focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-blue-500"
    const state = "disabled:opacity-80 disabled:cursor-not-allowed hover:brightness-110"

    const variants = {
        primary: "bg-blue-600 text-white",
        secondary: "bg-slate-200 text-slate-900",
        danger: "bg-red-600 text-white hover:bg-red-700",
        extra: "bg-green-600 text-white hover:bg-green-700",
    }

    return base + " " + focus + " " + state + " " + (variants[props.variant] || variants.primary)
})
</script>
<template>
    <div class="w-full">
    <label
    v-if="label"
    :for="id"
    class="mb-1 block text-sm font-medium text-slate-700"
    >
        {{ label }}
    </label>
    </div>

    <div class="relative">
        <input
        v-bind:id="id"
        v-bind:type="type"
        v-bind:placeholder="placeholder"
        v-bind:disabled="disabled"
        v-bind:value="modelValue"
        v-bind:aria-invalid="error ? 'true' : 'false'"
        v-bind:aria-describedby="helperId"
        v-on:input="$emit('update:modelValue', $event.target.value)"
        v-on:@focus="$emit('focus')"
        v-on:@blur="$emit('blur')"
        v-bind:class="inputClasses"
        />

    <span 
    v-if="error"
    class="pointer-events-none absolute right-3 top-1/2 -translate-y-1/2 text-xs font-medium text-red-600"
    >
        !
    </span>
    </div>

    <p
    v-if="helperText"
    v-bind:id="helperId"
    class="mt-1 text-xs"
    v-bind:class="error ? 'text-red-600' : 'text-slate-500'"
    >
    {{ helperText }}
    </p>
</template>

<script>
import { computed } from 'vue';
export default {
    name:'BaseInput',
    props: {
        modelValue: {type: String, default: ''},
        label: {type: String, default: ''},
        id: {type: String, default: ''},
        placeholder: {type: String, default: ''},
        disabled : {type: Boolean, default: false},
        error: {type: Boolean, default: false},
        helperText: {type: String, default: ''},
        type: {type: String, default: 'text'},
        variant: {
            type: String,
            default: 'default',
            validator: validacion => ['default', 'success', 'danger'].includes(validacion),
        },
            size: {
            type: String,
            default: 'md',
            validator: vald => ['sm', 'md', 'lg'].includes(vald),
        },
    },
    emits: ['update:modelValue', 'focus', 'blur'],


    setup(props) {
        const safeId = computed(() => props.id || `input-${Math.random().toString(36).slice(2, 7)}`)
        const helperId = computed(() => `${safeId.value}-help`)
    const inputClasses = computed(function() {
        const base =
            'block w-full rounded-md outline-none transition placeholder-slate-400 ' +
            'bg-white text-slate-900 ring-1 ring-inset ' +
            'focus:ring-2 focus:ring-offset-0 disabled:cursor-not-allowed disabled:opacity-60'
        
        const sizes = {
            sm: 'px-2 py-1 text-sm',
            md: 'px-3 py-2 text-sm',
            lg: 'px-4 py-3 text-base',
        }

        const variants = {
            default: 'ring-slate-300 focus:ring-blue-500',
            success: 'ring-emerald-400 focus:ring-emerald-500',
            danger: 'ring-red-400 focus:ring-red-500',
        }
        const intent = props.error ? variants.danger : variants[props.variant]
        return base + " " + (sizes[props.size]) + " " + intent
        })
        return { inputClasses, helperId, id: safeId }
    },
}

</script>
<script setup lang="ts">
const variants = {
  default: 'border border-gray-200 hover:bg-gray-100',
  danger: 'bg-red-200 enabled:hover:bg-red-100',
} as const

type Veriant = keyof typeof variants
const { variant = 'default' } = defineProps<{
  variant?: Veriant
}>()
defineEmits(['click'])
</script>

<template>
  <button
    :class="['text-sm font-medium rounded-full px-3 py-1', variants[variant]]"
    @click="$emit('click')"
  >
    <slot> OK </slot>
  </button>
</template>

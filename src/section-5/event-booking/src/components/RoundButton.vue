<script setup lang="ts">
defineEmits(['click'])
</script>

<template>
  <button
    class="text-sm font-medium border border-gray-200 rounded-full px-3 py-1 hover:bg-gray-100"
    @click="$emit('click')"
  >
    <slot> OK </slot>
  </button>
</template>

<script setup lang="ts">
import RoundButton from './RoundButton.vue'
defineEmits(['click'])
</script>

<template>
  <RoundButton class="bg-red-200" @click="$emit('click')">Cancel</RoundButton>
</template>

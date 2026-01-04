<script setup lang="ts">
import RoundButton from '@/components/RoundButton.vue'
import RoundedCard from '@/components/RoundedCard.vue'
;('@/components/RoundButton.vue')

defineProps<{
  title: string
  when: string
  description: string
}>()

defineEmits(['register'])
</script>

<template>
  <div>
    <RoundedCard>
      <h3 class="p-4 font-medium text-xl border-b border-gray-200">{{ title }}</h3>
      <p class="p-4 border-b border-gray-200">{{ when }}</p>
      <p class="p-4">{{ description }}</p>

      <section class="flex justify-end p-4">
        <RoundButton @click="$emit('register')"> Register </RoundButton>
      </section>
    </RoundedCard>
  </div>
</template>

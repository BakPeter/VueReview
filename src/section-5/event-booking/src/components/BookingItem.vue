<script setup lang="ts">
import CancelButton from '@/components/CancelButton.vue'
import RoundedCard from '@/components/RoundedCard.vue'

defineProps<{
  description: string
  statusValue: string
}>()
defineEmits(['cancelBooking'])
</script>
<template>
  <RoundedCard>
    <div class="grid grid-cols-2 items-center">
      <p class="p-4">
        {{ description }} - Status: {{ statusValue === 'true' ? 'OK' : 'CANCELED' }}
      </p>
      <section class="flex justify-end p-4">
        <CancelButton @click="console.log('Cancel')" />
      </section>
    </div>
  </RoundedCard>
</template>

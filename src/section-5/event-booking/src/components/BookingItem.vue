<script setup lang="ts">
import SectionCard from '@/components/SectionCard.vue'
import RoundButton from './RoundButton.vue'

defineProps<{
  description: string
  statusValue: string
}>()
defineEmits(['cancelBooking'])
</script>
<template>
  <SectionCard>
    <!-- <div class="grid grid-cols-2 items-center">
      <p>{{ description }} - Status: {{ statusValue === 'true' ? 'OK' : 'CANCELED' }}</p>
      <section class="flex justify-end">
        <CancelButton @click="console.log('Cancel')" />
      </section>
    </div> -->

    <div class="flex justify-between">
      <div>
        <p>{{ description }} - Status: {{ statusValue === 'true' ? 'OK' : 'CANCELED' }}</p>
      </div>
      <section class="flex justify-end">
        <RoundButton variant="danger">Cancel</RoundButton>
      </section>
    </div></SectionCard
  >
</template>

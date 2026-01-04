<script setup lang="ts">
<<<<<<< HEAD
=======
import CancelButton from '@/components/CancelButton.vue'
// import RoundedCard from '@/components/RoundedCard.vue'
>>>>>>> b7dd9a78c75679ecb73d9d26bd21b1979d2e3504
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
<<<<<<< HEAD
    <div class="flex justify-between">
      <div>
        <p>{{ description }} - Status: {{ statusValue === 'true' ? 'OK' : 'CANCELED' }}</p>
      </div>
      <section class="flex justify-end">
        <RoundButton variant="danger">Cancel</RoundButton>
=======
    <!-- <div class="grid grid-cols-2 items-center">
      <p>{{ description }} - Status: {{ statusValue === 'true' ? 'OK' : 'CANCELED' }}</p>
      <section class="flex justify-end">
        <CancelButton @click="console.log('Cancel')" />
>>>>>>> b7dd9a78c75679ecb73d9d26bd21b1979d2e3504
      </section>
    </div> -->

    <div class="flex justify-between">
      <div>
        <p>{{ description }} - Status: {{ statusValue === 'true' ? 'OK' : 'CANCELED' }}</p>
      </div>
      <section class="flex justify-end">
        <RoundButton variant="danger">Cancel</RoundButton>
      </section>
    </div>
  </SectionCard>
</template>

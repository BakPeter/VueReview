<script setup lang="ts">
import SectionCard from '@/components/SectionCard.vue'
import RoundButton from '@/components/RoundButton.vue'
import { LoaderCircle, Check } from 'lucide-vue-next'
import { computed } from 'vue'

const props = defineProps<{
  title: string
  status: string
}>()

const pending = computed(() => props.status === 'pending')
const icon = computed(() => (pending.value ? LoaderCircle : Check))

defineEmits(['cancelBooking'])
</script>
<template>
  <SectionCard>
    <div class="flex justify-between">
      <div class="flex space-x-2">
        <div>{{ title }}</div>
        <div>
          <component
            :is="icon"
            :class="{ 'animate-spin text-red-400': pending, 'text-green-400': !pending }"
          />
        </div>
      </div>
      <RoundButton variant="danger" @click="$emit('cancelBooking')">Cancel</RoundButton>
    </div>
  </SectionCard>
</template>

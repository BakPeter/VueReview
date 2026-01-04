<script setup lang="ts">
import EventCard from '@/components/EventCard.vue'
import BookingItem from './components/BookingItem.vue'
</script>

<template>
  <main class="container mx-auto my-8 space-y-">
    <h1 class="text-4xl font-medium">Event Booking App</h1>
    <h2 class="text-2xl font-medium">All Events</h2>
    <section class="grid grid-cols-2 gap-8">
      <EventCard
        v-for="i in 8"
        v-bind:key="i"
        title="Vue Confrenence 2024"
        when="2024-05-01"
        description="Conferencce about Vue"
        @register="console.log('Registered!')"
      />
    </section>
    <h2 class="text-2xl font-medium pt-6 pb-4">Your Booking</h2>
    <section class="grid grid-cols-1 gap-4">
      <BookingItem
        v-for="i in 3"
        :key="i"
        description="Booking item"
        statusValue="false"
        @cancel-booking="console.log('Event Cancel: ' + i)"
      />
    </section>
  </main>
</template>

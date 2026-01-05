<script setup lang="ts">
import { ref, onMounted } from 'vue'
import EventCard from '@/components/EventCard.vue'
import BookingItem from '@/components/BookingItem.vue'
import LoadingEventCard from '@/components/LoadingEventCard.vue'
import LoadingBookngItem from './components/LoadingBookngItem.vue'

type Event = {
  id: string
  title: string
  date: string
  description: string
  location: string
}

type Booking = {
  id: string
  userId: number
  eventId: string
  eventTitle: string
  status: string
}

const events = ref<Event[]>([])
const eventloading = ref(false)

const bookings = ref<Booking[]>([])
const bookingsLoading = ref(false)

const fetchEventsAsync = async () => {
  try {
    eventloading.value = true
    const response = await fetch('http://localhost:3001/events')
    events.value = await await response.json()
    console.log(events.value)
  } finally {
    eventloading.value = false
  }
}

const fetchBookingsAsync = async () => {
  try {
    bookingsLoading.value = true
    const response = await fetch('http://localhost:3001/bookings')
    bookings.value = await await response.json()
    console.log(bookings.value)
  } finally {
    bookingsLoading.value = false
  }
}

onMounted(() => {
  fetchEventsAsync()
  fetchBookingsAsync()
})
const handleRegistrationAsync = async (event: Event) => {
  const newBooking: Booking = {
    id: Date.now().toString(),
    userId: 1,
    eventId: event.id,
    eventTitle: event.title,
    status: 'confirmed',
  }

  await fetch('http://localhost:3001/bookings', {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json',
    },
    body: JSON.stringify(newBooking),
  })
}
</script>

<template>
  <main class="container mx-auto my-8 space-y-">
    <h1 class="text-4xl font-medium">Event Booking App</h1>
    <h2 class="text-2xl font-medium">All Events</h2>
    <section class="grid grid-cols-2 gap-8">
      <template v-if="!eventloading">
        <EventCard
          v-for="eventItem in events"
          v-bind:key="eventItem.id"
          :title="eventItem.title"
          :when="eventItem.date"
          :description="eventItem.description"
          @register="handleRegistrationAsync(eventItem)"
        />
      </template>
      <template v-else>
        <LoadingEventCard v-for="i in 4" :key="i" />
      </template>
    </section>
    <h2 class="text-2xl font-medium pt-6 pb-4">Your Booking</h2>

    <section class="grid grid-cols-1 gap-4">
      <template v-if="bookingsLoading">
        <LoadingBookngItem v-for="i in 3" :key="i" />
      </template>
      <template v-else
        ><BookingItem
          v-for="item in bookings"
          :key="item.id"
          :description="item.eventTitle"
          :statusValue="item.status"
          @cancelBooking="console.log('Event Cancel: ' + item.id)"
      /></template>
    </section>
  </main>
</template>

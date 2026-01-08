<script setup lang="ts">
import { ref, onMounted } from 'vue'
import BookingItem from '@/components/BookingItem.vue'
import LoadingBookngItem from '@/components/LoadingBookngItem.vue'
import EventList from '@/components/EventList.vue'
import type { Event } from '@/types/Event'

type Booking = {
  id: string
  userId: number
  eventId: string
  eventTitle: string
  status: string
}

const bookings = ref<Booking[]>([])
const bookingsLoading = ref(false)

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
const findBookingById = (id: string) => bookings.value.findIndex((b) => b.eventId === id)

const cancelBookingAsync = async (bookingId: string) => {
  const index = findBookingById(bookingId)
  const originalBooking = bookings.value[index]
  bookings.value.splice(index, 1)

  try {
    const response = await fetch(`http://localhost:3001/bookings/${originalBooking!.id}`, {
      method: 'DELETE',
    })

    if (!response.ok) {
      throw new Error('Booking could not be cancel')
    }
  } catch (error) {
    console.log('Failed to cancel booking:', error)
    bookings.value.splice(index, 0, originalBooking!)
  }
}

onMounted(() => {
  fetchBookingsAsync()
})

const handleRegistrationAsync = async (event: Event) => {
  if (bookings.value.some((item) => item.eventId === event.id)) {
    alert('You Are Already Registered For This Event')
    return
  }

  const newBooking: Booking = {
    id: Date.now().toString(),
    userId: 1,
    eventId: event.id,
    eventTitle: event.title,
    status: 'pending',
  }

  bookings.value.push(newBooking)

  try {
    const response = await fetch('http://localhost:3001/bookings', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
      },
      body: JSON.stringify({ ...newBooking, status: 'confirmed' }),
    })

    if (response.ok) {
      const index = findBookingById(newBooking.eventId)
      bookings.value[index] = await response.json()
    } else {
      throw new Error('Failed To Confirm Booking')
    }
  } catch (error) {
    console.log(error)
    bookings.value = bookings.value.filter((item) => item.id !== newBooking.id)
  }
}
</script>

<template>
  <main class="container mx-auto my-8 space-y-">
    <h1 class="text-4xl font-medium">Event Booking App</h1>
    <h2 class="text-2xl font-medium">All Events</h2>
    <EventList @register="handleRegistrationAsync($event)" />
    <h2 class="text-2xl font-medium pt-6 pb-4">Your Booking</h2>

    <section class="grid grid-cols-1 gap-4">
      <template v-if="bookingsLoading">
        <LoadingBookngItem v-for="i in 3" :key="i" />
      </template>
      <template v-else
        ><BookingItem
          v-for="item in bookings"
          :key="item.id"
          :title="item.eventTitle"
          :status="item.status"
          @cancelBooking="cancelBookingAsync(item.eventId)"
      /></template>
    </section>
  </main>
</template>

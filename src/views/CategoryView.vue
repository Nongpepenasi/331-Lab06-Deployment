<script setup lang="ts">
import Category from '../components/Category.vue'
// import { events } from '@/events';
import type { EventItem } from '@/type'
import { ref, type Ref} from 'vue'
import EventService from '@/services/EventService'

const events: Ref<Array<EventItem>> = ref([])
  
  EventService.getEvent(6, 1).then((response) => {
    events.value = response.data
    console.log(events.value)
  })
</script>

<template>
  <div class="flex flex-col items-center text-right">
    <h1>This is a categories page</h1>
    <!-- <Category></Category> -->
    <div class="flex flex-col items-center text-right">
      <Category v-for="event in events" :key="event.id" :event="event"></Category>
    </div>
  </div>
</template>

<style>

</style>

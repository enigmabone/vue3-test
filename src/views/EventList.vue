<template>
  <div class="events">
   <h1>Events List</h1>
   <EventCard v-for="event in events" :key="event.id" :event="event"/>
  </div>
</template>

<script>
import EventCard from "@/components/EventCard"
import EventService from "@/services/EventService.js"

export default {
  name: "EventList",
  components: {
    EventCard
  },
  data() {
    return {
events: null
    }
  },
  created() {
    EventService.getEvents().then(response => {
      this.events = response.data
    }).catch(error => {
      console.log(error)
    })
  }
};
</script>
<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}
h1 {
  color: #096ce4;
}
</style>

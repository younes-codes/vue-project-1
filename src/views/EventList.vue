<template>
  <div class="events">
    <ul class="events-card-container">
      <EventCard v-for="event in events" :key="event.id" :event="event" />
    </ul>
  </div>
</template>

<script>
import EventCard from "@/components/EventCard.vue";
import EventService from "@/services/EventService.js";

export default {
  name: "EventList",
  components: {
    EventCard
  },
  data() {
    return {
      events: null
      //loading: true
    };
  },
  created() {
    EventService.getEvents()
      .then(response => {
        this.events = response.data;
      })
      .catch(error => {
        console.log(error);
      });
  }
};
</script>

<style scoped>
.events-card-container {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>

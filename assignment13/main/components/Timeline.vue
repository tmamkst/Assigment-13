<!-- Timeline.vue -->
<template>
    <div class="timeline">
      <div v-for="event in sortedEvents" :key="event.date" class="event">
        <div class="event-info">
          <h3>{{ event.title }}</h3>
          <p class="date">{{ event.date }}</p>
          <p>{{ event.description }}</p>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      events: Array
    },
    computed: {
      sortedEvents() {
        return this.events.sort((a, b) => new Date(a.date) - new Date(b.date));
      }
    }
  };
  </script>
  
  <style scoped>
  .timeline {
    display: flex;
    align-items: flex-start;
  }
  
  .event {
    border: 1px solid #ccc;
    padding: 15px;
    margin: 10px;
    border-radius: 5px;
    background-color: #f9f9f9;
  }
  
  .event-info {
    text-align: left;
  }
  
  .date {
    font-weight: bold;
    color: #888;
  }
  </style>
  
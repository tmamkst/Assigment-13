<template>
  <div id="app">
    <Timeline :events="eventsData" />

    <Accordion :accordionItems="accordionItems">
      <template v-slot:content="{ item }">
        <p>{{ item.title }} - {{ item.description }}</p>
      </template>
    </Accordion>

    <Carousel>
      <Slide v-for="slide in carouselItems" :key="slide.id">
        <div class="carousel__item">
          <img :src="slide.src" :alt="slide.alt"/>
        </div>
      </Slide>

      <template #addons>
        <Navigation />
        <Pagination />
      </template>
    </Carousel>
  </div>
</template>

<script>
import Timeline from "./components/Timeline.vue";
import Accordion from "./components/Accordion.vue";
import { defineComponent } from 'vue'
import { Carousel, Navigation, Pagination, Slide } from 'vue3-carousel'

import 'vue3-carousel/dist/carousel.css'

export default defineComponent({
  components: {
    Timeline,
    Accordion,
    Carousel,
    Slide,
    Navigation,
    Pagination
  },
  data() {
    return {
      eventsData: [
        {
          title: "Event 1",
          date: "2023-01-01",
          description: "Description for Event 1"
        },
        {
          title: "Event 2",
          date: "2023-02-15",
          description: "Description for Event 2"
        },
        {
          title: "Event 3",
          date: "2023-03-30",
          description: "Description for Event 3"
        }
      ],
      accordionItems: [
        { name: "section1", title: "Section 1" },
        { name: "section2", title: "Section 2" },
        { name: "section3", title: "Section 3" }
      ],
      carouselItems: [
        { id: "1", src: "./assets/image1.jpg", alt: "Image 1" },
        { id: "2", src: "./assets/image2.jpg", alt: "Image 2" },
        { id: "3", src: "./assets/image3.jpg", alt: "Image 3" }
      ]
    };
  }
});
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  padding: 10px;
}

.carousel__item {
  min-height: 200px;
  width: 100%;
  background-color: var(--vc-clr-primary);
  color: var(--vc-clr-white);
  font-size: 20px;
  border-radius: 8px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.carousel__slide {
  padding: 10px;
}

.carousel__prev,
.carousel__next {
  box-sizing: content-box;
  border: 5px solid white;
}
</style>

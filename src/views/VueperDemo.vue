<template>
<div>
  <div>
    <h2>Banner demo</h2>
    <vueper-slides :dragging-distance="50">
      <vueper-slide v-for="(slide, i) in slides" :key="i" :style="{ 'background-image': `url(${slide.image}?v=${i})`}">
        <template #content>
          <div>
            <h3>{{ slide.title }}</h3>
            <p>{{ slide.content }}</p>
          </div>
        </template>
      </vueper-slide>
    </vueper-slides>
  </div>
  <div style="margin-top: 60px">
    <h2>PDP Demo</h2>
    <div class="temp-container">
      <div class="temp-container__column">
        <vueper-slides class="pdp-slides" :dragging-distance="50">
          <vueper-slide v-for="(slide, i) in (1*4)" :image="`https://picsum.photos/800?v=${i}`" :key="i" />
        </vueper-slides>
      </div>
      <div class="temp-container__column">
        PDP Content and stuff
      </div>
    </div>
    <div style="padding-bottom: 80px">
      Yooo padding time!
    </div>
  </div>
</div>
</template>

<script>
import {VueperSlides, VueperSlide } from 'vueperslides'
import 'vueperslides/dist/vueperslides.css'

export default {
  components: { VueperSlides, VueperSlide },
  data: () => ({
    slides: [{
      title: 'Title #1',
      content: 'Slide content #1',
      image: 'https://picsum.photos/1920/1080'
    },
    {
      title: 'Title #2',
      content: 'Slide content #2',
      image: 'https://picsum.photos/1920/1080'
    }]
  })
}
</script>

<style lang="scss" scoped>
.temp-container {
  display: flex;
  margin-bottom: 20px;

  &__column {
    flex: 1;
  }
}

.pdp-slides {
  .vueperslide  {
    transform: translateX(70px);
  }
}
</style>
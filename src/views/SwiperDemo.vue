<template>
<div>
  <div>
    <h2>Banner demo</h2>
    <swiper :loop="true">
      <swiper-slide v-for="(slide, i) in slides" :key="i" class="custom-slide" :style="{ 'background-image': `url(${slide.image}?v=${i})`}">
        <template>
          <h3>{{ slide.title }}</h3>
          <p>{{ slide.content }}</p>
        </template>
      </swiper-slide>
    </swiper>
  </div>
  <div style="margin-top: 60px">
    <h2>PDP Demo</h2>
    <div class="temp-container">
      <div class="temp-container__column">
        <swiper :slidesPerView="'auto'" :spaceBetween="0" :loop="true" :rtl="true" class="pdp-slides">
          <swiper-slide v-for="(slide, i) in (1*4)" :key="i">
            <img :src="`https://picsum.photos/650?v=${i}`" />
          </swiper-slide>
        </swiper>
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
import Swiper from '../components/Swiper'
import SwiperSlide from '../components/SwiperSlide'

export default {
  components: { Swiper, SwiperSlide},
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
  overflow: hidden;
  width: 100%;

  &__column {
    width: 50%;
  }
}

.custom-slide {
  padding: 15% 0;
}

.pdp-slides {
  .swiper-slide { width: 85%; }
}
</style>
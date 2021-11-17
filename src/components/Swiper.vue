<template>
  <div :dir="rtl ? 'rtl': null" class="swiper">
    <div class="swiper-wrapper">
      <slot />
    </div>
    <div ref="navigationNext" class="swiper-button-next"></div>
    <div ref="navigationPrev" class="swiper-button-prev"></div>
    <div ref="pagination" class="swiper-pagination"></div>
  </div>
</template>

<script>
import Swiper, { Navigation, Pagination } from 'swiper'
import 'swiper/swiper-bundle.css'

export default {
  props: {
    loop: {
      type: Boolean,
      default: false
    },
    slidesPerView: {
      default: null
    },
    spaceBetween: {
      type: Number,
      default: 0
    },
    rtl: {
      type: Boolean,
      default: false
    }
  },
  mounted() {
    const opts = {
      loop: this.loop,
      navigation: {
        nextEl: this.$refs.navigationNext,
        prevEl: this.$refs.navigationPrev
      },
      pagination: {
        el: this.$refs.pagination,
        clickable: true
      },
      spaceBetween: this.spaceBetween
    }

    if (this.slidesPerView)
      opts.slidesPerView = this.slidesPerView
    
    Swiper.use([Navigation, Pagination])

    const $swiper = new Swiper(this.$el, opts)
  }
}
</script>

<style lang="scss" scoped>

</style>
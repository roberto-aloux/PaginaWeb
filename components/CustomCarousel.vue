<template>
  <div class="custom-carousel">
    <div class="carousel-container" :style="{ transform: `translateX(-${currentIndex * 100}%)` }">
      <div class="slide" v-for="(image, index) in carouselImages" :key="index">
        <img :src="image.src" :alt="image.alt || 'Carousel Image'">
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      currentIndex: 0,
      intervalId: null,
      carouselImages: [
        { src: '/imagenes/bannerImg1.png'},
        { src: '/imagenes/bannerImg2.jpg'},
        { src: '/imagenes/bannerImg3.jpeg'}
      ]
    };
  },
  methods: {
    nextSlide() {
      this.currentIndex = (this.currentIndex + 1) % this.carouselImages.length;
    },
    startAutoSlide() {
      this.intervalId = setInterval(this.nextSlide, 3000);
    },
    stopAutoSlide() {
      clearInterval(this.intervalId);
      this.intervalId = null;
    }
  },
  mounted() {
    this.startAutoSlide();
  },
  beforeDestroy() {
    this.stopAutoSlide();
  }
};
</script>

<style scoped>
.custom-carousel {
  position: relative;
  max-width: 100%;
  overflow: hidden;
}

.carousel-container {
  display: flex;
  transition: transform 0.5s ease;
}

.slide {
  flex: 0 0 100%;
}

img {
  width: 100%;
  height: auto;
}
</style>

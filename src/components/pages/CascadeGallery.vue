<template>
  <div class="cascade-gallery">
    <div 
      v-for="(img, index) in images" 
      :key="index" 
      class="gallery-item"
      :class="{ 'active': activeIndex === index }"
      @mouseover="activeIndex = index"
      @mouseleave="activeIndex = null"
    >
      <img :src="img.src" :alt="img.alt">
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      activeIndex: null,
      images: [
        { src: '/assets/image1.jpg', alt: 'Image 1' },
        { src: '/assets/image2.jpg', alt: 'Image 2' },
        { src: '/assets/image3.jpg', alt: 'Image 3' },
      ],
    };
  },
};
</script>

<style scoped>
.cascade-gallery {
  display: flex;
  height: 400px;
  position: relative;
  margin: 0 auto;
  width: 80%;
}

.gallery-item {
  position: absolute;
  height: 100%;
  transition: all 0.3s ease;
  overflow: hidden;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}

/* Начальные позиции */
.gallery-item:nth-child(1) { left: 0; width: 60%; z-index: 3; }
.gallery-item:nth-child(2) { left: 40%; width: 50%; z-index: 2; }
.gallery-item:nth-child(3) { left: 70%; width: 40%; z-index: 1; }

/* Стили при наведении */
.gallery-item.active {
  width: 70% !important;
  z-index: 4 !important;
}

/* Сужение соседних картинок */
.gallery-item:nth-child(1).active ~ .gallery-item:nth-child(2) { left: 70%; width: 30%; }
.gallery-item:nth-child(1).active ~ .gallery-item:nth-child(3) { left: 85%; width: 15%; }

.gallery-item:nth-child(2).active ~ .gallery-item:nth-child(3) { left: 85%; width: 15%; }
.gallery-item:nth-child(2).active ~ .gallery-item:nth-child(1) { width: 30%; }

.gallery-item:nth-child(3).active ~ .gallery-item:nth-child(1) { width: 40%; }
.gallery-item:nth-child(3).active ~ .gallery-item:nth-child(2) { width: 40%; }

img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}
</style>
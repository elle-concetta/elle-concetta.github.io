<template>
    <section class="card" id="gallery">
        <div class="container">
            <div class="col ">
                <h2 class="h2"><i>Our</i> Moments</h2>
                <p>From our first date, adventurous trips, to our engagement.</p>
            </div>
          <div class="col">
            <div class="grid justify-items-center gap-4">
              <div class="main-image-container">
                <img
                    class="h-auto max-w-full rounded-lg"
                    :src="mainImage"
                    alt=""
                    :style="{ animation: slideAnimation }">
              </div>
              <div class="grid grid-cols-5 gap-4">
                <div v-for="(image, index) in images" :key="index">
                  <img
                      class="h-auto max-w-full rounded-lg cursor-pointer"
                      :src="image"
                      alt=""
                      @click="showImage(index)">
                </div>
              </div>
            </div>
          </div>
        </div>
    </section>
</template>
<script setup lang="ts">
import { ref, watch } from 'vue';

const mainImage = ref('/public/img/gallery_eng-1.png');
const images = [
  '/public/img/gallery_firstdate.jpg',
  '/public/img/gallery_bday.JPG',
  '/public/img/gallery_cenotes.png',
  '/public/img/gallery_cenote2.png',
  '/public/img/gallery_athens.JPG',
  '/public/img/gallery_grboat.jpg',
  '/public/img/gallery_mykonos.JPG',
  '/public/img/gallery_santorini.JPG',
  '/public/img/pantheon-italy.JPG',
  '/public/img/eng-20.png'
];

const showImage = (index) => {
  mainImage.value = images[index];
};

const slideAnimation = ref('');
let currentIndex = 0;
setInterval(() => {
  currentIndex = (currentIndex + 1) % images.length;
  mainImage.value = images[currentIndex];
}, 5000);

watch(mainImage, () => {
  slideAnimation.value = 'slide-in 0.5s ease forwards';
});
</script>
<style scoped>

@import url('https://use.typekit.net/fyp0lzh.css');

@font-face {
  font-family: 'Mier A';
  src: url('src/assets/mier/MierA-Regular.eot');
  src: local('Mier A Regular'), local('MierA-Regular'),
  url('src/assets/mier/MierA-Regular.eot?#iefix') format('embedded-opentype'),
  url('src/assets/mier/MierA-Regular.woff2') format('woff2'),
  url('src/assets/mier/MierA-Regular.woff') format('woff'),
  url('src/assets/mier/MierA-Regular.ttf') format('truetype');
  font-weight: normal;
  font-style: normal;
}

@font-face {
  font-family: 'Mier A Demi';
  src: url('src/assets/mier/MierA-DemiBold.eot');
  src: local('Mier A DemiBold'), local('MierA-DemiBold'),
  url('src/assets/mier/MierA-DemiBold.eot?#iefix') format('embedded-opentype'),
  url('src/assets/mier/MierA-DemiBold.woff2') format('woff2'),
  url('src/assets/mier/MierA-DemiBold.woff') format('woff'),
  url('src/assets/mier/MierA-DemiBold.ttf') format('truetype');
  font-weight: 600;
  font-style: normal;
}

h2 {
  text-align: center;
  font-family: "freight-big-pro", serif !important;
  font-size: 39px;
}

h3 {
  text-align: center;
  font-family: "Mier A Demi", sans-serif !important;
  font-style: italic;
  font-size: x-large;
}

p {
  text-align: center;
  font-family: "Mier A", sans-serif !important;
  font-size: medium;
}

.main-image-container {
    position: relative;
}

@keyframes slide-in {
    from {
        opacity: 0;
        transform: translateX(100%);
    }
    to {
        opacity: 1;
        transform: translateX(0%);
    }
}
.main-image {
    width: 100%;
    max-width: 100%;
    height: auto;
}
</style>

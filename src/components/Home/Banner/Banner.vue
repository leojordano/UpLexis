<template>
  <div class="banner-principal">
    <VueSlickCarousel v-bind="this.slideSettings">
      <SlideItem
        v-for="slide in slides" :key="slide.id"
        :title="slide.title"
        :description="slide.description"
        :price="slide.price"
        :backgroundImageUrl="slide.image"
      />
    </VueSlickCarousel>
  </div>
</template>

<script>

// import { defineComponent } from 'vue';
import VueSlickCarousel from 'vue-slick-carousel';
import SlideItem from '@/components/Home/SlideItem/SlideItem.vue';

import 'vue-slick-carousel/dist/vue-slick-carousel.css';
import 'vue-slick-carousel/dist/vue-slick-carousel-theme.css';

export default {
  name: 'Banner',
  components: {
    SlideItem,
    VueSlickCarousel,
  },
  data() {
    return {
      slides: [
        {
          id: 1, title: 'Lorem Ipsum 1', description: 'Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industrys standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book.', price: '40,00', image: 'https://w7.pngwing.com/pngs/275/820/png-transparent-trend-pattern-background-textured-textures-black-texture-poster-banner.png',
        },
        {
          id: 2, title: 'Lorem Ipsum 2', description: 'Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industrys standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book.', price: '40,00', image: 'https://w7.pngwing.com/pngs/275/820/png-transparent-trend-pattern-background-textured-textures-black-texture-poster-banner.png',
        },
        {
          id: 3, title: 'Lorem Ipsum 3', description: 'Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industrys standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book.', price: '40,00', image: 'https://w7.pngwing.com/pngs/275/820/png-transparent-trend-pattern-background-textured-textures-black-texture-poster-banner.png',
        },
        {
          id: 4, title: 'Lorem Ipsum 4', description: 'Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industrys standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book.', price: '40,00', image: 'https://w7.pngwing.com/pngs/275/820/png-transparent-trend-pattern-background-textured-textures-black-texture-poster-banner.png',
        },
      ],
      slideSettings: {
        dots: false,
        arrows: false,
        edgeFriction: 0.35,
        infinite: true,
        speed: 500,
        slidesToShow: 1,
        slidesToScroll: 1,
      },
    };
  },
};
</script>

<style lang="scss" scoped src="./Banner.scss"></style>

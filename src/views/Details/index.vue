<template>
  <div class="details">
    <Banner />
    <div class="details__container">

      <div class="details__header">
        <router-link
          to="/"
          class="details__header__story"
        >
          <img :src="HeaderArrowIcon" alt=""> Histórico Empresarial
        </router-link>
      </div>

      <div class="details__header__post-name">
        <span>{{ Item.name }}</span>
      </div>

      <div class="details__body">
        <div class="details__body__carousel">
          <button @click="showPrev" class="carousel__prev-arrow">
            <img :src="SlideArrowIcon" alt="">
          </button>
          <VueSlickCarousel ref="carousel" :arrows="true" v-bind="this.slideSettings">
            <div v-for="slide in slides" class="carousel__slide" :key="slide.id">
              <img :src="slide.img" :alt="slide.text">
              <p>{{ slide.text }}</p>
            </div>
          </VueSlickCarousel>
          <button @click="showNext" class="carousel__prev-next">
            <img :src="SlideArrowIcon" alt="">
          </button>
        </div>

        <div class="details__body__description">
          <p>{{ this.Item.description }}</p>
        </div>
      </div>

      <div class="details__footer">
        <div class="details__footer__price">
          <span class="price--little">R$</span>
          <span class="price--bigger">{{ this.Item.price }}</span>
        </div>

        <CustomButton label="Habilitar" to="/" />
      </div>

    </div>
  </div>
</template>

<script>
import VueSlickCarousel from 'vue-slick-carousel';
import Banner from '@/components/Home/Banner/Banner.vue';
import SimpleArrow from '@/assets/icons/Simple-Arrow.svg';
import SlideArrow from '@/assets/icons/Slide-Arrow.svg';
import Cards from '@/assets/Cards';
import CustomButton from '@/components/Utils/Button/CustomButton.vue';

import 'vue-slick-carousel/dist/vue-slick-carousel.css';
import 'vue-slick-carousel/dist/vue-slick-carousel-theme.css';

export default {
  components: {
    Banner,
    VueSlickCarousel,
    CustomButton,
  },
  data() {
    return {
      Item: Cards.find((x) => x.id === Number(this.$route.params.id)),
      windowWidth: window.innerWidth,
      slideSettings: {
        dots: false,
        prevArrow: false,
        nextArrow: false,
        edgeFriction: 0.35,
        infinite: true,
        speed: 500,
        slidesToShow: this.isMobile() ? 1 : 2,
        slidesToScroll: this.isMobile() ? 1 : 2,
      },
      slides: [
        { id: 1, img: 'https://w7.pngwing.com/pngs/275/820/png-transparent-trend-pattern-background-textured-textures-black-texture-poster-banner.png', text: 'Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industrys standard dummy text ever since the 1500s,' },
        { id: 2, img: 'https://w7.pngwing.com/pngs/275/820/png-transparent-trend-pattern-background-textured-textures-black-texture-poster-banner.png', text: 'Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industrys standard dummy text ever since the 1500s,' },
        { id: 3, img: 'https://w7.pngwing.com/pngs/275/820/png-transparent-trend-pattern-background-textured-textures-black-texture-poster-banner.png', text: 'Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industrys standard dummy text ever since the 1500s,' },
      ],
      HeaderArrowIcon: SimpleArrow,
      SlideArrowIcon: SlideArrow,
    };
  },
  methods: {
    showNext() {
      this.$refs.carousel.next();
    },
    showPrev() {
      this.$refs.carousel.prev();
    },
    isMobile() {
      if (/Android|webOS|iPhone|iPad|iPod|BlackBerry|IEMobile|Opera Mini/i.test(navigator.userAgent)) {
        return true;
      }
      return false;
    },
  },
};
</script>

<style scoped lang="scss" src="./Details.scss"></style>

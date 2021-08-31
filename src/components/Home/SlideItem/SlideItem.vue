<template>
  <div class="slide__item" :style="{ background: `url(${backgroundImageUrl})`}" >
    <div class="slide__item__container">
      <h2 class="slide__item__title">
        {{ title }}
      </h2>

      <p class="slide__item__descrition">
        {{ description }}
      </p>

      <div class="slide__item__price">
        <div>
          <span class="slide__item__price--little">R$</span>
          <span class="slide__item__price--bigger">{{ price }}</span>
        </div>

        <CustomButton class="slide__item__price__button" label="Saiba Mais" To="/" />
      </div>
    </div>
  </div>
</template>

<script>

import CustomButton from '../../Utils/Button/CustomButton.vue';

export default {
  components: { CustomButton },
  props: {
    title: String,
    description: String,
    price: String,
    backgroundImageUrl: String,
  },
};
</script>

<style lang="scss" src="./SlideItem.scss" scoped>

</style>

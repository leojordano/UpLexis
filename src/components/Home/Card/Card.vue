<template>
  <div class="card">
    <div class="card__body">
      <div class="card__body__icon">
        <img :src="this.Icon" :alt="Title">
      </div>

      <div class="card__body__title">{{ Title }}</div>

      <div class="card__body__description">{{ Description.substring(0,250) }}</div>
    </div>

    <div class="card__footer">
      <span class="card__footer__price">R$ {{ Price }}</span>
      <router-link class="card__footer__link" :to="'/'+To">Saiba mais</router-link>
    </div>
  </div>
</template>

<script>
import Categories from '@/assets/Categories';

export default {
  props: {
    Category: Number,
    Title: String,
    Description: String,
    Price: String,
    To: String,
  },
  data() {
    return {
      Icon: null,
    };
  },
  mounted() {
    this.Icon = Categories.find((x) => x.id === this.Category)?.icon;
  },
};
</script>

<style lang="scss" scoped src="./Card.scss"></style>

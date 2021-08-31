<template>
  <div
    v-on:click="handleChecked()"
    :class="CheckedValue"
    class="check-category"
  >
    <span class="check-category__icon">
      <img :src="this.Icon" alt="">
    </span>
    <span class="check-category__title">{{ Title }}</span>
  </div>
</template>

<script>

import Categories from '@/assets/Categories';
import Hammer from '@/assets/icons/Hammer.svg';

export default {
  props: {
    Title: String,
    Id: Number,
    CheckedValue: String,
  },
  data() {
    return {
      Icon: Hammer,
    };
  },

  methods: {

    handleChecked() {
      this.checked = !this.checked;
    },
  },

  created() {
    this.Icon = Categories.find((x) => x.funcName === this.Title)?.icon ?? Hammer;
  },
};
</script>

<style scoped lang="scss" src="./CheckCategory.scss"></style>

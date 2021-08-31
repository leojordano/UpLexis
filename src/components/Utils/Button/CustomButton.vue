<template>
  <div class="custom-bottom">
    <router-link :to="To">{{ label }}</router-link>
  </div>
</template>

<script>

export default {
  props: {
    label: String,
    To: String,
  },
};
</script>

<style lang="scss" scoped src="./CustomButton.scss">

</style>

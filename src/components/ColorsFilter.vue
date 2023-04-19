<template>
  <ul class="colors" :class="{ 'colors--black': blackOn }">
    <li class="colors__item" v-for="color in productColors" :key="color.id">
      <label class="colors__label">
        <input class="colors__radio sr-only" type="radio" :name="`${productId}_color`"
               :value="color.id" v-model="checkedColorId">
        <span class="colors__value" :style="{backgroundColor: color.code}"></span>
      </label>
    </li>
  </ul>
</template>

<script>

export default {
  name: 'ColorsFilter',
  data() {
    return {
      checkedColorId: null,
    };
  },
  model: {
    prop: 'defaultColorId',
    event: 'changeColorId',
  },
  props: [
    'defaultColorId',
    'blackOn',
    'productId',
    'productColors',
  ],
  watch: {
    checkedColorId(newValue) {
      this.$emit('changeColorId', newValue);
    },
    defaultColorId(value) {
      this.checkedColorId = value;
    },
  },
  created() {
    this.checkedColorId = this.defaultColorId;
  },
};
</script>

<style scoped>

</style>

<template>
  <button class="btn" :class="{'btn-checked': isSelected}">
    <preloader-buttons v-if="isLoader"/>
    <div v-else class="main__item__content__price__is-selected">
      <img v-show="isSelected" src="../../public/img/buyCheck.svg" alt="Купленно">
      <h4>{{ isSelected ? 'В корзине' : 'Купить'}}</h4>
    </div>
  </button>
</template>


<script>
import PreloaderButtons from './Preloader-Buttons.vue';
export default {
  name: 'ItemCard',
  components: {
    PreloaderButtons
  },
  props: {
    isSelected: {
      type: Boolean,
      required: true
    },
    isLoader: {
      type: Boolean,
      required: false
    }
  },
}
</script>
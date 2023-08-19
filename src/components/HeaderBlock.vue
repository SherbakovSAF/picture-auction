<template>
  <header class="navigation__block container">
    <nav-module />
    <div class="navigation__block__user-active">
      <header-block-input @searchCardValue="$emit('searchCardValue', $event)"/>
      <div class="navigation__block__user-active__basket__wrap">
        <img src="../../public/img/basket.svg" alt="Купить картины">
        <div 
          v-show="selectedCardCount > 0" 
          class="navigation__block__user-active__count__shop">
          <p>{{ selectedCardCount }}</p>
        </div>
      </div>
    </div>
  </header>
</template>

<script>
import HeaderBlockInput from './HeaderBlock-input';
import NavModule from './NavModule';

export default {
  name: 'HeaderBlock',
  components: {
    HeaderBlockInput,
    NavModule
  },
  props: {
    selectedCardCount: {type: Number, required: false,}
  },
  emits: ['searchCardValue'],
}
</script>
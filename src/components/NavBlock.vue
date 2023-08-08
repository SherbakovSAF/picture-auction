<template>
    <header class="navigation__block container">
    <div class="navigation__block__information">
      <img src="../../public/img/logo-museum.svg" alt="Музей имени ...">
      <nav>
        <ul>
          <li><a href="#"><h5>Каталог</h5></a></li>
          <li><a href="#"><h5>Доставка</h5></a></li>
          <li><a href="#"><h5>Оплата</h5></a></li>
          <li><a href="#"><h5>Контакты</h5></a></li>
          <li><a href="#"><h5>О галерее</h5></a></li>
        </ul>
      </nav>
    </div>
    <div class="navigation__block__user-active">
      <nav-block-input />
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
import NavBlockInput from './NavBlock-input';

export default {
  name: 'HeaderBlock',
  components: {
    NavBlockInput
  },
  props: {
    selectedCardCount: {
      type: Number,
      required: false,
    }
  },
  data(){
    return {
      searchInput: '',
    }
  },
}
</script>
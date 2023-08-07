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
      <header-block-input />
      <div class="navigation__block__user-active__basket__wrap">
        <img src="../../public/img/basket.svg" alt="Купить картины">
        <!-- <div 
          v-show="filterSelectedItem.length" 
          class="navigation__block__user-active__count__shop">
          <p>{{ filterSelectedItem.length }}</p>
        </div> -->
        <div 
        
          class="navigation__block__user-active__count__shop">
          
        </div>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: 'HeaderBlock',
  data(){
    return {
      searchInput: '',
    }
  },
  computed: {
    // filterSelectedItem() {
    //   return this.itemState.filter(e=> e.isSelected == true)
    // },
  },
}
</script>
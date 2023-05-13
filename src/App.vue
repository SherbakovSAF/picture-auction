<template>
<div class="main__wrap">
  <header class="navigation__block container">
    <div class="navigation__block__information">
      <img src="../public/img/logo-museum.svg" alt="Музей имени ...">
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
      <input type="text" placeholder="Поиск по названию картины" v-model="searchInput">
      <button @click="itemStateFilterInput" class="btn">Найти</button>
      <div class="navigation__block__user-active__basket__wrap">
        <img src="../public/img/basket.svg" alt="Купить картины">
        <div v-if="filterSelectedItem.length" class="navigation__block__user-active__count__shop"><p>{{ filterSelectedItem.length }}</p></div>
      </div>
    </div>
  </header>
  <hr>
  <main class="container">
    <h1 class="main__title">Картины эпохи Возрождения</h1>
    <div class="main__item__wrap">
      <article :class="{'main__item-sold': card.isSales}" v-for="card in filterItemState" :key="card.id">
        <div class="main__item__content__wrap">
          <img :src="card.image" :alt="card.title">
          <h2>{{ card.title }}</h2>
          <div v-if="!card.isSales" class="main__item__content__interaction">
            <div class="main__item__content__price__wrap">
              <h6 class="main__item__content__price-sale">
                {{card.pastPrice > 0 ? zeroSeparation(card.pastPrice) + " $" : ''}} 
              </h6>
              <h3>{{ zeroSeparation(card.currentPrice) }} $</h3>
            </div>
            <button v-if="card.isSelected" 
            @click="sendRequest(card)" class="btn btn-checked">
              <div v-if="card.isLoader" class="lds-dual-ring"></div>
              <div v-else class="main__item__content__price__is-selected" >
                <img src="../public/img/buyCheck.svg" alt="">
                <h4>В корзине</h4>
              </div>
            </button>
            <button v-else
            @click="sendRequest(card)" class="btn">
              <div v-if="card.isLoader" class="lds-dual-ring"></div>
              <h4 v-else>Купить</h4>
            </button>
            
          </div>
          <h3 class="main__item__content__sales-title">{{ card.isSales ? 'Проданно на аукционе' : ''}}</h3>
        </div>
      </article>
    </div>
  </main>
<footer>
  <div class="footer__block container">
    <div class="footer__block__information">
      <img src="../public/img/logo-museum.svg" alt="">
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
    <div class="footer__block__contact">
      <a href="tel:8495999999999"><h5 class="footer__block__contact__number">+7 (495) 999-99-99</h5></a>
      <a target="_blank" href="https://yandex.ru/maps/193/voronezh/house/ulitsa_nikitina_119/Z0AYcw5kTUwCQFtrfXR2eHRqZw==/?ll=39.594495%2C51.879893&utm_source=share&z=17"><h5 class="footer__block__contact__address">г. Воронеж, ул. Никитина, 119А</h5></a>
    </div>
  </div>
</footer>
</div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      itemState: [
        {
          id: 1,
          isSales: false,
          image: `./img/cardImage/venera.jpg`,
          title: 'Рождение Венеры» Сандро Боттичелли',
          pastPrice: 2000000,
          currentPrice: 1000000,
          isLoader: false,
          isSelected: true,
        },
        {
          id: 2,
          isSales: false,
          image: `./img/cardImage/vechere.jpg`,
          title: 'Тайная вечеря»  Леонардо да Винчи',
          pastPrice: null,
          currentPrice: 1000000,
          isLoader: false,
          isSelected: false,
        },
        {
          id: 3,
          isSales: false,
          image: `./img/cardImage/makeadam.jpg`,
          title: 'Сотворение Адама Микеланджело',
          pastPrice: 6000000,
          currentPrice: 1000000,
          isLoader: false,
          isSelected: false,
        },
        {
          id: 4,
          isSales: true,
          image: `./img/cardImage/kill.jpg`,
          title: 'Урок анатомии»  Рембрандт',
          pastPrice: 2000,
          currentPrice: 1000000,
          isLoader: false,
          isSelected: false,
        }
      ],
      searchInput: '',
      filterItemState: []
    }
  },
  computed: {
    filterSelectedItem() {
      return this.itemState.filter(e=> e.isSelected == true)
    },

    // Я сначала сделал без нажатия на кнопку, а потом увидил что я и кнопку оказывается делал)
    // itemStateFilterInput(){
    //   return this.itemState.filter(e=> e.title.toLowerCase().includes(this.searchInput.toLowerCase()))
    // }
  },
  methods: {
    async sendRequest(item) {
      item.isLoader = true
      let response = await fetch("https://jsonplaceholder.typicode.com/posts/1")
      item.isLoader = false
      if (response.ok) {
        this.addItemInBasket(item)
        alert('Запрос удачный');
        
      } else {
        alert('Запрос неудался');
      }
      localStorage.setItem('itemState', JSON.stringify(this.itemState))
    },
    addItemInBasket(item) {
      item.isSelected = !item.isSelected
    },
    zeroSeparation(num){
      var n = num.toString();
      var separator = " ";
      return n.replace(/(\d{1,3}(?=(?:\d\d\d)+(?!\d)))/g, "$1" + separator);
    },
      itemStateFilterInput(){
      this.filterItemState = this.itemState.filter(e=> e.title.toLowerCase().includes(this.searchInput.toLowerCase()))
    }
  },
  mounted: function(){
    let localStorageItemState = JSON.parse(localStorage.getItem('itemState'))
    if(localStorageItemState) {
      this.itemState = JSON.parse(localStorage.getItem('itemState'))
    }

    this.filterItemState = [...this.itemState]
  }
}
</script>

<style src="./scss/index.scss" lang="scss">

</style>

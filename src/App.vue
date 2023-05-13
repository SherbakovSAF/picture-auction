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
      <input type="text" name="" id="" placeholder="Поиск по названию картины">
      <button class="btn">Найти</button>
      <div class="navigation__block__user-active__basket__wrap">
        <img src="../public/img/basket.svg" alt="Купить картины">
        <div class="navigation__block__user-active__count__shop"><p>1</p></div>
      </div>
    </div>
  </header>
  <hr>
  <main class="container">
    <h1 class="main__title">Картины эпохи Возрождения</h1>
    <div class="main__item__wrap">
      <article v-for="card in itemState" :key="card.id">
        <div class="main__item__content__wrap">
          <img :src="card.image" :alt="card.title">
          <h2>{{ card.title }}</h2>
          <div v-if="!card.isSales" class="main__item__content__interaction">
            <div class="main__item__content__price__wrap">
              <h6 class="main__item__content__price-sale">
                {{card.pastPrice > 0 ? card.pastPrice + " $" : ''}} 
              </h6>
              <h3>{{ card.currentPrice }} $</h3>
            </div>
            <button @click="sendRequest(card)" class="btn">
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
        },
        {
          id: 2,
          isSales: false,
          image: `./img/cardImage/vechere.jpg`,
          title: 'Рождение Венеры» Сандро Боттичелли',
          pastPrice: null,
          currentPrice: 1000000,
          isLoader: false,
        },
        {
          id: 3,
          isSales: false,
          image: `./img/cardImage/makeadam.jpg`,
          title: 'Рождение Венеры» Сандро Боттичелли',
          pastPrice: 6000000,
          currentPrice: 1000000,
          isLoader: false,
        },
        {
          id: 4,
          isSales: true,
          image: `./img/cardImage/kill.jpg`,
          title: 'Рождение Венеры» Сандро Боттичелли',
          pastPrice: 2000,
          currentPrice: 1000000,
          isLoader: false,
        }
      ],
      searchInput: ''
    }
  },
  methods: {
    async sendRequest(item) {
      item.isLoader = true
      let response = await fetch("https://jsonplaceholder.typicode.com/posts/1")
      item.isLoader = false
      response.ok ? alert('Запрос удачный') : alert('Запрос неудался')
    }
  }
}
</script>

<style src="./scss/main.scss" lang="scss">

</style>

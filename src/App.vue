<template>
<div class="container">
  <header class="navigation__block">
    <div class="navigation__block__information">
      <img src="" alt="">
      <nav>
        <ul>
          <li><a href="#"><h4>Каталог</h4></a></li>
          <li><a href="#"><h4>Доставка</h4></a></li>
          <li><a href="#"><h4>Оплата</h4></a></li>
          <li><a href="#"><h4>Контакты</h4></a></li>
          <li><a href="#"><h4>О галерее</h4></a></li>
        </ul>
      </nav>
    </div>
    <div class="navigation__block__user-active">
      <input type="text" name="" id="" placeholder="Поиск по названию картины">
      <button class="btn">Найти</button>
      <div class="navigation__block__user-active__basket__wrap">
        <img src="" alt="">
        <div class="navigation__block__user-active__count__shop"><p>1</p></div>
      </div>
    </div>
  </header>
  <main>
    <h1 class="main__title">Картины эпохи Возрождения</h1>
    <div class="main__item__wrap">
      <article>
        <div class="main__item__content__wrap">
          <img src="" alt="">
          <h2>«Рождение Венеры» Сандро Боттичелли</h2>
          <div class="main__item__content__price__wrap">
            <p class="main__item__content__price-sale"></p>
            <h4>1 000 000 $</h4>
            <h3>1 000 000 $</h3>
            <button class="btn">Купить</button>
          </div>
          <h3 class="main__item__content__sales-title">Продано на аукционе</h3>
        </div>
      </article>
    </div>
  </main>
  <footer>
    <div class="footer__block__information">
      <img src="" alt="">
      <nav>
        <ul>
          <li><a href="#"><h4>Каталог</h4></a></li>
          <li><a href="#"><h4>Доставка</h4></a></li>
          <li><a href="#"><h4>Оплата</h4></a></li>
          <li><a href="#"><h4>Контакты</h4></a></li>
          <li><a href="#"><h4>О галерее</h4></a></li>
        </ul>
      </nav>
    </div>
    <div class="footer__block__contact">
      <a href="tel:8495999999999"><h5>+7 (495) 999-99-99</h5></a>
      <a href="tel:8495999999999"><h5>г. Воронеж, ул. Никитина, 119А</h5></a>

    </div>
  </footer>
</div>
</template>

<script>


export default {
  name: 'App',
  data() {
    return {
      searchInput: ''
    }
  }
}
</script>

<style src="./scss/main.scss" lang="scss">

</style>

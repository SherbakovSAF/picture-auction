<template>
  <footer>
    <div class="footer__block container">
    <nav-module class="footer__block__nav"/>
      <div class="footer__block__contact">
        <a href="tel:8495999999999"><h5 class="footer__block__contact__number">+7 (495) 999-99-99</h5></a>
        <a target="_blank" href="https://yandex.ru/maps/193/voronezh/house/ulitsa_nikitina_119/Z0AYcw5kTUwCQFtrfXR2eHRqZw==/?ll=39.594495%2C51.879893&utm_source=share&z=17"><h5 class="footer__block__contact__address">г. Воронеж, ул. Никитина, 119А</h5></a>
      </div>
    </div>
  </footer>
</template>

<script>
import NavModule from './NavModule';

export default {
  name: 'FooterBlock',
  components: {
    NavModule
  },
}
</script>
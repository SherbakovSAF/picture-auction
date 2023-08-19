<template>
  <div class="navigation__block__information">
    <img src="../../public/img/logo-museum.svg" alt="Музей имени ...">
      <nav>
        <HamburgUI :isOpen="isOpen" @toggleOpen="isOpen = $event"/>
        <Transition>
          <ul :style="{display: isOpen ? 'flex' : 'none'}">
          <li><a href="#"><h5>Каталог</h5></a></li>
          <li><a href="#"><h5>Доставка</h5></a></li>
          <li><a href="#"><h5>Оплата</h5></a></li>
          <li><a href="#"><h5>Контакты</h5></a></li>
          <li><a href="#"><h5>О галерее</h5></a></li>
        </ul>
        </Transition>
      </nav>
    
  </div>
</template>

<script>
import HamburgUI from '@/components/UI/HamburgUI.vue'
export default {
  name: 'NavModule',
  components: {
    HamburgUI
  },
  data(){
    return{
      isOpen: false
    }
  },
  methods: {
    calcWindow(){
      document.documentElement.clientWidth < 560 ? this.isOpen = false : this.isOpen = true
    }
  },

  mounted(){
    this.calcWindow()
    window.addEventListener('resize', this.calcWindow)
    
  }
}
</script>
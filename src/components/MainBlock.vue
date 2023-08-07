<template>
  <main class="container">
    <h1 class="main__title">Картины эпохи Возрождения</h1>
    <div class="main__item__wrap">
      <article :class="{ 'main__item-sold': card.isSales }" 
        v-for="card in filterItemState" :key="card.id">
        <div class="main__item__content__wrap">
          <img class="main__item__content__img" :src="card.image" :alt="card.title">
          <h2>{{ card.title }}</h2>
          <div v-if="!card.isSales" class="main__item__content__interaction">
            <div class="main__item__content__price__wrap">
              <h6 class="main__item__content__price-sale">
                {{ card.pastPrice > 0 ? zeroSeparation(card.pastPrice) + " $" : '' }}
              </h6>
              <h3>{{ zeroSeparation(card.currentPrice) }} $</h3>
            </div>
            <button v-if="card.isSelected" @click="sendRequest(card)" class="btn btn-checked">
              <div v-if="card.isLoader" class="lds-dual-ring"></div>
              <div v-else class="main__item__content__price__is-selected">
                <img src="../../public/img/buyCheck.svg" alt="">
                <h4>В корзине</h4>
              </div>
            </button>
            <button v-else @click="sendRequest(card)" class="btn">
              <div v-if="card.isLoader" class="lds-dual-ring"></div>
              <h4 v-else>Купить</h4>
            </button>

          </div>
          <h3 v-show="card.isSales" class="main__item__content__sales-title">Проданно на аукционе</h3>
        </div>
      </article>
    </div>
  </main>
</template>

<script>
export default {
  name: 'MainBlock',
  data(){
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
      filterItemState: []
    }
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
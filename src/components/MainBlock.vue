<template>
  <main class="container">
    <h1 class="main__title">Картины эпохи Возрождения</h1>
    <div class="main__item__wrap">
      <item-card 
        v-for="card in cardFiltering" 
        :cardInfo="card" 
        :key="card.id"
        :isSelected="card.isSelected"
        @updateIsSelected="card.isSelected = $event"/>
    </div>
  </main>
</template>

<script>
import ItemCard from './ItemCard'

export default {
  name: 'MainBlock',
  components: {
    ItemCard
  },
  props: {
    searchCardValue: {type: String, required: false}
  },
  emits: ['updateCard'],
  data(){
    return {
      cardState: [
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
    }
  },
  methods: {
    emitUpdateState() {
      const selectedCard = this.cardState.filter(e => e.isSelected)
      this.$emit('updateCard', selectedCard.length)
    },
  },
  computed: {
    cardFiltering() {
      return this.cardState
      .filter(e => e.title.toLowerCase().includes(this.searchCardValue.toLowerCase()))
    },
  },
  watch: {
    cardState: {
      handler(){ 
        this.emitUpdateState()
      }, deep: true      
    },
  },

  mounted(){
    this.emitUpdateState()
    // let localStorageItemState = JSON.parse(localStorage.getItem('itemState'))
    // if(localStorageItemState) {
    //   this.itemState = JSON.parse(localStorage.getItem('itemState'))
    // }

    // this.filterItemState = [...this.itemState]
  }
}
</script>
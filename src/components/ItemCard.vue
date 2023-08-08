<template>
  <article :class="{ 'main__item-sold': cardInfo.isSales }">
    <div class="main__item__content__wrap">
      <img class="main__item__content__img" :src="cardInfo.image" :alt="cardInfo.title">
      <h2>{{ cardInfo.title }}</h2>
      <div class="main__item__content__interaction" v-if="!cardInfo.isSales">
        <div class="main__item__content__price__wrap">
          <h6 class="main__item__content__price-sale">
            {{ zeroSeparation }}
          </h6>
          <h3>{{ cardInfo.currentPrice }} $</h3>
        </div>
        <ItemCardButtons @click="sendRequest()" :isSelected="cardInfo.isSelected" :isLoader="isLoader" />
      </div>
      <h3 class="main__item__content__sales-title" v-else>
        Проданно на аукционе
      </h3>
    </div>
  </article>
</template>

<script>
import ItemCardButtons from './ItemCard-buttons.vue'

export default {
  name: 'ItemCard',
  components: {
    ItemCardButtons
  },
  props: {
    cardInfo: {
      type: Object,
      required: true
    },
    isSelected: {
      type: Boolean
    }
  },
  emits: ['updateIsSelected'],
  data(){
    return {
      isLoader: false
    }
  },
  computed: {
    zeroSeparation(){
      const priceToString = String(this.cardInfo.pastPrice);
      const separation = priceToString.replace(/(\d{1,3}(?=(?:\d\d\d)+(?!\d)))/g, "$1" + " ");
      return this.cardInfo.pastPrice  > 0 ? separation + " $" : ''
    },
  },
  methods: {
    async sendRequest() {
      this.isLoader = true
      await fetch("https://jsonplaceholder.typicode.com/posts/1")
        .then(this.trueRes)
        .catch(this.falseRes)
      this.isLoader = false
    },
    trueRes(){
      this.addItemInBasket()
      alert('Запрос удачный');
    },
    falseRes(){
      alert('Запрос неудался');
    },
    addItemInBasket() {
      this.$emit('updateIsSelected', !this.isSelected)
    },
    
  }
}
</script>
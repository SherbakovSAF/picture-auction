<template>
<div class="main__wrap">
  <header-block 
    :selectedCardCount="selectedCardCount"
    @searchCardValue="searchCardValue = $event"/>
  <hr>
  <main-block 
  @updateCard="selectedCardCount = $event"
  :searchCardValue="searchCardValue"
  />
  <footer-block />
</div>
</template>

<script>
import HeaderBlock from '@/components/HeaderBlock'
import MainBlock from '@/components/MainBlock'
import FooterBlock from '@/components/FooterBlock'
export default {
  name: 'App',
  components: {
    HeaderBlock,
    MainBlock,
    FooterBlock
  },
  data(){
    return {
      selectedCardCount: 0,
      searchCardValue: ''
    }
  },
}
</script>

<style src="./assets/scss/index.scss" lang="scss">

</style>

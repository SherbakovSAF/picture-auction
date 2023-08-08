<template>
<div class="main__wrap">
  <nav-block :selectedCardCount="selectedCardCount"/>
  <hr>
  <main-block @updateCard="selectedCardCount = $event"/>
  <footer-block />
</div>
</template>

<script>
import NavBlock from '@/components/NavBlock'
import MainBlock from '@/components/MainBlock'
import FooterBlock from '@/components/FooterBlock'
export default {
  name: 'App',
  components: {
    NavBlock,
    MainBlock,
    FooterBlock
  },
  data(){
    return {
      selectedCardCount: 0
    }
  },
}
</script>

<style src="./assets/scss/index.scss" lang="scss">

</style>

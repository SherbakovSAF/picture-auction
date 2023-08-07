<template>
<div class="main__wrap">
  <header-block />
  <hr>
  <main-block />
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
}
</script>

<style src="./assets/scss/index.scss" lang="scss">

</style>

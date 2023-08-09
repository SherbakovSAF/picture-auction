<template>
    <input v-model="searchInput"
      type="text" 
      placeholder="Поиск по названию картины">
    <button @click="$emit('searchCardValue', this.searchInput)" class="btn">Найти</button>
</template>

<script>
export default {
  name: 'NavBlock-input',
  props: ['modelValue'],
  emits: ['searchCardValue'],
  data(){
    return {
      searchInput: ''
    }
  },
}
</script>
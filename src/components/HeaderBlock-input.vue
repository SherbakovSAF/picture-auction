<template>
    <input
      :value='modelValue' @input="$emit('@update:modelValue', $event.target.value)"
      type="text" 
      placeholder="Поиск по названию картины">
    <button @click="itemStateFilterInput" class="btn">Найти</button>
</template>

<script>
export default {
  name: 'HeaderBlock',
  props: ['modelValue'],
  emits: ['@update:modelValue'],
}
</script>
<template>
    <label class="hamburg__wrap">
      <input type="checkbox" :checked="isOpen" @click="$emit('toggleOpen', !isOpen)">
      <div>
        <span class="hamburgItem"></span>
        <span class="hamburgItem"></span>
        <span class="hamburgItem"></span>
      </div>
    </label>
</template>

<script>
export default {
  name: 'HamburgUI',
  props: {isOpen: {type: Boolean, required: true}},
  emits: ['toggleOpen']
}
</script>
<template>
  <button type="button" :class="className">
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: 'Button',
  props: {
    className: String
  }
}
</script>

<style scoped>

</style>

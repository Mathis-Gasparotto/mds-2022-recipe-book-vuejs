<template>
  <li class="recipe-ingredient">
    <label :class="'shopping-list-item' + (shoppingItem.checked ? ' shopping-list-item--checked' : '')">
      <input type="checkbox" :checked="shoppingItem.checked" @input="$emit('checkShoppingListItem', shoppingItem.id)"/> {{ shoppingItem.label }}
    </label>
  </li>
</template>

<script>
export default {
  name: 'ShoppingListItem',
  props: {
    shoppingItem: Object
  }
}
</script>

<style scoped>

</style>

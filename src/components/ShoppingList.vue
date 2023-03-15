<template>
  <div class="shopping-list">
    <h2 class="shopping-list-title">Shopping list</h2>
    <ul class="recipe-ingredients-list">
      <ShoppingListItem v-for="shoppingItem in shoppingList" :key="shoppingItem.id" :shoppingItem="shoppingItem" @checkShoppingListItem="(id) => $emit('checkShoppingListItem', id)" />
    </ul>
    <div class="shopping-list-actions">
      <Button className="shopping-list-clear-button" @click="$emit('checkAllShoppingListItem')">Check all</Button>
      <Button className="shopping-list-clear-button" @click="$emit('clearCheckedShoppingListItem')">Clear checked items</Button>
      <Button className="shopping-list-clear-button" @click="$emit('clearAllShoppingListItem')">Clear all</Button>
    </div>
  </div>
</template>

<script>
import ShoppingListItem from './ShoppingListItem.vue'
import Button from './Button.vue'
export default {
  name: 'ShoppingList',
  props: {
    shoppingList: Array
  },
  components: {
    ShoppingListItem,
    Button
  }
}
</script>

<style scoped>

</style>

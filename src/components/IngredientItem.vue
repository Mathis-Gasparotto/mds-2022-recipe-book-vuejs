<template>
  <li class="recipe-ingredient">
    <input type="text" class="recipe-ingredient-input" :value="ingredient.label" @input="(event) => $emit('updateIngrediantLabel', event.target.value)" />
    <button class="recipe-ingredient-delete-button" @click="$emit('deleteIngredient', ingredient)">🗑</button>
  </li>
</template>

<script>
export default {
  name: 'IngredientItem',
  props: {
    ingredient: Object
  }
}
</script>

<style scoped>

</style>

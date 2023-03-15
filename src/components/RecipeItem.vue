<template>
  <div class="recipe">
  <div class="recipe-title">{{ recipe.title }}</div>
  <div class="recipe-actions">
    <Button className="recipe-edit-button" @click="$emit('editRecipe')">Edit</Button>
    <Button className="recipe-delete-button" @click="$emit('deleteRecipe')">Delete</Button>
  </div>
</div>
</template>

<script>
import Button from './Button.vue'
export default {
  name: 'RecipeItem',
  props: {
    recipe: Object
  },
  components: { 
    Button
  }
}
</script>

<style scoped>

</style>

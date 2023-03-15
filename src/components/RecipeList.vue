<template>
  <div class="recipe-book">
    <RecipeItem v-for="recipe in recipes" :key="recipe.id" :recipe="recipe" 
      @editRecipe="$emit('editRecipe', recipe)"
      @deleteRecipe="$emit('deleteRecipe', recipe.id)"
    />
  </div>
</template>

<script>
import RecipeItem from './RecipeItem.vue'
export default {
  name: 'RecipeList',
  components: { 
    RecipeItem 
  },
  props: {
    recipes: [Object]
  }
}
</script>

<style scoped>

</style>

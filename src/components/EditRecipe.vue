<template>
  <div className="recipe-edit-form">
    <input type="text" class="recipe-edit-title-input" v-model="newRecipe.title"/>
    <textarea rows={10} class="recipe-edit-description-input" v-model="newRecipe.desc"/>
    <h2 class="recipe-ingredients-title">Ingredients</h2>
    <IngredientsList 
      :ingredients="recipe.ingredients" 
      @deleteIngredient="(ingredient) => $emit('deleteIngredient', ingredient)"
      @updateIngredient="(id, value) => newRecipe.ingredients.find((e) => e.id === id).label = value"
      @addIngredient="(value) => $emit('addIngredient', value)"
    />
    <div class="recipe-edit-actions">
      <button class="recipe-edit-save-button" type="button" @click="$emit('updateRecipe', newRecipe)">Save</button>
      <button class="recipe-edit-cart-button">Add to shopping list</button>
    </div>
  </div>
</template>

<script>
import IngredientsList from './IngredientsList.vue'
export default {
  name: 'EditRecipe',
  components: {
    IngredientsList
  },
  props: {
    recipe: Object
  },
  data () {
    return {
      newRecipe: {}
    }
  },
  created () {
    this.newRecipe = {...this.recipe}
  }
}
</script>

<style scoped>

</style>

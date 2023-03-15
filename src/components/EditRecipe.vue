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
      <Button className="recipe-edit-exit-button" @click="$emit('exit')">Exit</Button>
      <Button className="recipe-edit-save-button" @click="$emit('updateRecipe', newRecipe)">Save</Button>
      <Button className="recipe-edit-cart-button" @click="$emit('addToShoppingList')">Add to shopping list</Button>
    </div>
  </div>
</template>

<script>
import IngredientsList from './IngredientsList.vue'
import Button from './Button.vue'
export default {
  name: 'EditRecipe',
  components: {
    IngredientsList,
    Button
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
  },
  watch: {
    recipe() {
      this.newRecipe = {...this.recipe}
    }
  }
}
</script>

<style scoped>

</style>

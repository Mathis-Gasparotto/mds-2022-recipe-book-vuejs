<template>
  <div class="main">
    <h1 class="main-title">Recipe Book</h1>
    <AddRecipeForm @onSubmit="(title, desc) => addRecipe(title, desc)" />
    <RecipeList :recipes="recipes" 
      @editRecipe="(recipe) => recipeSelectedToEdit = recipe" 
      @deleteRecipe="(id) => deleteRecipe(id)"
    />
    <EditRecipe 
      v-if="recipeSelectedToEdit.id" 
      :recipe="recipeSelectedToEdit"
      @deleteIngredient="(ingredient) => deleteIngredient(ingredient, recipeSelectedToEdit.id)"
      @updateRecipe="(newRecipe) => updateRecipe(recipeSelectedToEdit.id, newRecipe)"
      @addIngredient="(value) => addIngredient(recipeSelectedToEdit.id, value)"
    />
  </div>
</template>

<script>
import AddRecipeForm from './components/AddRecipeForm.vue'
import RecipeList from './components/RecipeList.vue'
import EditRecipe from './components/EditRecipe.vue'
export default {
  components: {
    AddRecipeForm,
    RecipeList,
    EditRecipe
  },
  data() {
    return {
      recipes: [
        {
          id: 1,
          title: 'Mon titre',
          desc: 'Oui',
          ingredients: [
            {
              id: 1,
              label: 'Ingredient 1'
            },
            {
              id: 2,
              label: 'Ingredient 2'
            },
          ]
        },
        {
          id: 2,
          title: 'Mon titre 2',
          desc: 'Oui 2',
          ingredients: [
            {
              id: 3,
              label: 'Ingredient 1'
            },
            {
              id: 4,
              label: 'Ingredient 2'
            },
          ]
        },
      ],
      recipeSelectedToView: {},
      recipeSelectedToEdit: {}
    }
  },
  methods: {
    addRecipe(title, desc) {
      this.recipes.push({
        id: Date.now(),
        title,
        desc,
        ingredients: []
      })
    },
    deleteIngredient(ingredient, recipeId) {
      const index = this.recipes.find((e) => e.id === recipeId).ingredients.indexOf(ingredient)
      this.recipes.find((e) => e.id === recipeId).ingredients.splice(index, 1)
    },
    updateRecipe (id, newData) {
      return console.log(newData)
      this.recipes.find((e) => e.id === id) = {
        ...newData,
        ingredients: [...newData.ingredients]
      }
      this.recipeSelectedToEdit = {}
    },
    addIngredient (recipeId, label) {
      this.recipes.find((e) => e.id === recipeId).ingredients.push({
        id: Date.now(),
        label
      })
    },
    deleteRecipe (id) {
      const index = this.recipes.indexOf(this.recipes.find((e) => e.id === id))
      this.recipes.splice(index, 1)
    }
  }
}
</script>

<style scoped></style>

<template>
  <ul class="recipe-ingredients-list">
    <IngredientItem 
      v-for="ingredient in ingredients" 
      :key="ingredient.id" 
      :ingredient="ingredient"
      @deleteIngredient="(ingredient) => $emit('deleteIngredient', ingredient)"
      @updateIngrediantLabel="(value) => $emit('updateIngredient', ingredient.id, value)"
    />
    <form class="recipe-new-ingredient" @submit.prevent="handleSubmit()">
      <input type="text" class="recipe-new-ingredient-input" placeholder="Add a new ingredient..." v-model="ingredientToAdd"/>
      <button class="recipe-new-ingredient-button" type="submit">Add</button>
    </form>
  </ul>
</template>

<script>
import IngredientItem from './IngredientItem.vue'
export default {
  name: 'IngredientsList',
  props: {
    ingredients: [Object]
  },
  components: {
    IngredientItem
  },
  data () {
    return  {
      ingredientToAdd: ''
    }
  },
  methods: {
    handleSubmit () {
      const toSend = this.ingredientToAdd.trim()
      if(!toSend.length) return
      this.ingredientToAdd = ''
      this.$emit('addIngredient', toSend)
    }
  }
}
</script>

<style scoped>

</style>

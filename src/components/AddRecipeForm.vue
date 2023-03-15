<template>
  <form @submit.prevent="handleSumbit" class="new-recipe-form">
    <input type="text" class="recipe-title-input" placeholder="Add a new recipe..." v-model="title"/>
    <textarea class="recipe-title-textarea" cols="30" rows="10" placeholder="Description..." v-model="description"></textarea>
    <button type="submit" class="recipe-create-button">Add</button>
  </form>
</template>

<script>
export default {
  name: 'AddRecipeForm',
  data () {
    return {
      title: '',
      description: ''
    }
  },
  methods: {
    handleSumbit () {
      const titleToSend = this.title.trim()
      const descToSend = this.description.trim()
      if (!titleToSend.length || !descToSend.length) return
      this.title = ''
      this.description = ''
      this.$emit('onSubmit', titleToSend, descToSend)
    }
  }
}
</script>

<style scoped>

</style>

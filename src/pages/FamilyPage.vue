<template>
    <div class="container recipe-details">
      <div v-if="recipes">
        <div v-for="recipe in recipes" :key="recipe.id">
            <h2 class="mb-4">{{ recipe.recipe_name }}</h2>
        <div class="row">
          <div class="col-md-6">
            <img :src="recipe.picture" :alt="recipe.title" class="recipe-image img-fluid mb-4">
          </div>
          <div class="col-md-6">
            <p class="mb-2">Owner: {{ recipe.owner_name }}</p>
            <p class="mb-2">Made In: {{ recipe.special_time}}</p>
          </div>
        </div>
  
        <h3 class="mt-4">Ingredients</h3>
        <ul class="list-group">
          <li class="list-group-item" v-for="ingredient in recipe.ingredients" :key="ingredient">{{ ingredient }}</li>
        </ul>
  
        <h3 class="mt-4">Instructions</h3>
        <ol class="list-group">
          <li class="list-group-item" v-for="step in recipe.instructions" :key="step" v-html="removeStepNumbering(step)"></li>
        </ol>
        </div>

      </div>
      <div v-else>
        <p>Loading recipe...</p>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        recipes: null
      };
    },
    mounted() {
      this.created();
    },
    methods: {
      async created() {
      try {
        let response;
        try {
          response = await this.axios.get(
            // "https://test-for-3-2.herokuapp.com/recipes/info",
            this.$root.store.server_domain + "/users/family-recipes",
          );
          if (response.status !== 200) this.$router.replace("/NotFound");
        } catch (error) {
          console.log("error.response.status", error.response.status);
          this.$router.replace("/NotFound");
          return;
        }
        this.recipes = response.data;
      } catch (error) {
        console.log(error);
      }
    },
    removeStepNumbering(step) {
        // Remove the step numbering from the instruction
        return step.replace(/^\d+\.\s*/, '');
      }
    }
    
  };
  </script>
  
  <style scoped>
  .recipe-details {
    max-width: 800px;
    margin: 0 auto;
  }
  
  .recipe-image {
    max-width: 100%;
    height: auto;
  }
  
  @media (max-width: 767.98px) {
    .recipe-image {
      max-width: 100%;
      height: auto;
    }
  }
  </style>
  
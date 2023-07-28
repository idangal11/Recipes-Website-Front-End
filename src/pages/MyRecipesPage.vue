<template>
    <div class="container">
      <b-container fluid>
        <!-- <h1 class="title">Main Page</h1> -->
        <b-row>
          <b-col v-if="$root.store.username">
            <RecipePreviewList
              v-if="personalRecipes.length > 0"
              title="Personal Recipes"
              :recipes="personalRecipes"
            />
            <div v-else>
              <!-- Show a message when there are no last watched recipes -->
              <p v-if="!loading">No personal recipes available.</p>
            </div>
            <div v-if="loading" class="spinner">
            <i class="fas fa-spinner fa-spin"></i>
          </div>
          </b-col>
  
        </b-row>
      </b-container>
  
      <!-- <router-link v-if="!$root.store.username" to="/login" tag="button">You need to Login to vue this</router-link> -->
  
    </div>
  </template>
  
  <script>
  // import { getRandomValues } from "crypto";
  import RecipePreviewList from "../components/RecipePreviewList";
  export default {
    name: "MainPage",
    components: {
      RecipePreviewList,
    },
    data() {
      return {
        personalRecipes: [],
        loading : false,
      };
    },
    async mounted() {
      this.updateRecipes();
    },
  
    methods: {
      async updateRecipes() {
        this.loading = true;
        try {
          if (this.$root.store.username) {
            const res = await this.axios.get(this.$root.store.server_domain+"/users/recipes_created"); 
            this.personalRecipes = res.data;
          }
        } catch (error) {
          console.log(error);
        }
        this.loading=false;
      },
  
    },
    
  };
  </script>
  
  
  
  <style lang="scss" scoped>
    .spinner {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100px;
    }

    .fa-spinner {
    animation: fa-spin 2s infinite linear;
    font-size: 80px;
    }

    @keyframes fa-spin {
    0% {
        transform: rotate(0deg);
    }
    100% {
        transform: rotate(360deg);
    }
    }
  </style>
  
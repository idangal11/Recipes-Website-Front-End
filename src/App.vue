<template>
  <div id="app">
    <div class="background-image-container">
      <nav class="navbar navbar-expand-lg navbar-light bg-light transparent-bg">
      <div class="container">
        <router-link :to="{ name: 'main' }" class="navbar-brand">
          <span class="logo-text">R&I Recipes</span>
        </router-link>
        <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarNav"
          aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarNav">
          <ul class="navbar-nav ml-auto">
            <li class="nav-item">
              <router-link :to="{ name: 'search' }" class="nav-link">Search</router-link>
            </li>
            <li class="nav-item">
              <router-link :to="{ name: 'about' }" class="nav-link">About</router-link>
            </li>
            <li v-if="!$root.store.username" class="nav-item">
              <router-link :to="{ name: 'register' }" class="nav-link">Register</router-link>
            </li>
            <li v-if="!$root.store.username" class="nav-item">
              <router-link :to="{ name: 'login' }" class="nav-link">Login</router-link>
            </li>
            
          <!-- Personal dropdown menu -->
          <li v-else class="nav-item dropdown">
            <a class="nav-link dropdown-toggle" href="#" role="button" @click="toggleDropdown" aria-haspopup="true" aria-expanded="false">
              Personal
            </a>
            <div class="dropdown-menu" :class="{ show: dropdownOpen }" aria-labelledby="navbarDropdown">
              <router-link :to="{ name: 'favorites' }" class="dropdown-item">My Favorites</router-link>
              <div class="dropdown-divider"></div>
              <router-link :to="{ name: 'myrecipes' }" class="dropdown-item">My Recipes</router-link>
              <div class="dropdown-divider"></div>
              <router-link :to="{ name: 'family' }" class="dropdown-item">My Family Recipes</router-link>
              <div class="dropdown-divider"></div>
              <b-button v-b-modal.modal-prevent-closing class="dropdown-item">Create Recipe</b-button>
            </div>
          </li>
            
            <!-- User info and logout -->
            <li v-if="$root.store.username" class="nav-item user-info">
              <span class="navbar-text">Logged in as: {{ $root.store.username }}</span>
              <button class="btn btn-primary ml-2" @click="logout">Logout</button>
            </li>
          </ul>
        </div>
        <RecipeModal></RecipeModal>
      </div>
    </nav>

    <div class="container py-4">
      <router-view />
    </div>
  </div>
</div>
</template>

<script>
import RecipeModal from "./components/RecipeModal.vue";
export default {
  name: "App",
  components: {
    RecipeModal,
  },
  data() {
    return {
      dropdownOpen: false,
    };
  },
  methods: {
    // Method to toggle the dropdown
    toggleDropdown() {
      this.dropdownOpen = !this.dropdownOpen;
    },
    logout() {
      this.$root.store.logout();
      this.$root.toast("Logout", "User logged out successfully", "success");

      this.$router.push("/").catch(() => {
        this.$forceUpdate();
      });
    },
  },
};
</script>

<style lang="scss" scoped>

/* Set the navbar colors and size */

.navbar-brand,
.navbar-nav .nav-link {
  color: #fff !important;
  font-weight: bold;
}

.navbar-brand:hover,
.navbar-nav .nav-link:hover {
  color: #00bfff !important;
}

/* Active link */
.navbar-nav .active > .nav-link {
  color: #00bfff !important;
}

/* Personal dropdown menu */
.personal-dropdown-button {
  color: #fff;
  background-color: #222;
  border-color: #00bfff;
}

/* Divider */
.navbar-divider {
  border-color: #00bfff;
}

/* User info and logout */
.user-info .btn {
  background-color: #00bfff;
  border-color: #00bfff;
  color: #fff;
}

.user-info .btn:hover {
  background-color: #0099cc;
  border-color: #0099cc;
  color: #fff;
}

/* Recipe Modal */
.modal-content {
  background-color: #222;
  color: #fff;
}

/* Rest of your existing styles... */

.transparent-bg {
  background-color: transparent !important;
  color:red;
}

.container{
  color: #fff;
}
</style>
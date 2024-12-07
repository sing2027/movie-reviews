<template>
  <nav class="navbar navbar-expand-lg navbar-dark bg-color shadow-sm w-100 p-2">
    <a class="navbar-brand" href="#">Movie Reviews</a>
    <button
      class="navbar-toggler"
      type="button"
      @click="toggleNavbar"
      :aria-expanded="isNavbarOpen ? 'true' : 'false'"
      aria-label="Toggle navigation"
    >
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" :class="{'show': isNavbarOpen}" id="navbarNav">
      <ul class="navbar-nav ms-auto">
        <li class="nav-item">
          <router-link to="/" class="nav-link active">Home</router-link>
        </li>
      </ul>
    </div>
  </nav>
</template>

<script>
export default {
  data() {
    return {
      isNavbarOpen: false,
    };
  },
  methods: {
    toggleNavbar() {
      this.isNavbarOpen = !this.isNavbarOpen;
    },
  },
};
</script>

<style scoped>
.navbar {
  font-family: 'Arial', sans-serif;
  transition: background-color 0.3s ease;
  width: 100%;
}

.bg-color {
  background: linear-gradient(135deg, #043C51, #043C51);
}

.navbar-brand {
  font-size: 1.8rem;
  font-weight: 700;
  color: #f8f9fa !important;
  transition: color 0.3s ease;
}

.navbar-brand:hover {
  color: #ff5c8d !important;
}

.navbar-nav .nav-item {
  margin-left: 20px;
}

.nav-link {
  font-size: 1.1rem;
  font-weight: 500;
  color: #f8f9fa;
  transition: color 0.3s ease, transform 0.3s ease;

}

.nav-link:hover {
  color: #ffffff;
  transform: scale(1.1);
}

.navbar-toggler-icon {
  background-color: transparent;
}

.nav-link.active {
  font-weight: bold;
  color: #ff5c8d !important;
}

@media (max-width: 991px) {
  .navbar-nav {
    text-align: center;
  }
  .navbar-collapse {
    width: 100%;
  }
}
</style>

<template>
  <div>
  
    <NavbarComponent />

   
    <div class="content">
      <router-view />
    </div>

    <FooterComponent />
  </div>
</template>

<script>
import NavbarComponent from "./components/NavbarComponent.vue";
import FooterComponent from "./components/FooterComponent.vue";

export default {
  components: {
    NavbarComponent,
    FooterComponent,
  },
};
</script>

<style scoped>
.content {
  min-height: calc(100vh - 100px); 
}
</style>

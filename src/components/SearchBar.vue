<template>
    <div class="app">
      <input
        type="text"
        class="form-control search-bar mt-4"
        v-model="searchQuery"
        @input="onSearch"
        placeholder="Search reviews..."
      />
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        searchQuery: '',
      };
    },
    methods: {
      onSearch() {
        this.$emit('search', this.searchQuery);
      },
    },
  };
  </script>
  
  <style scoped>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
  
  body {
    font-family: 'Arial', sans-serif;
    background: linear-gradient(135deg, #ff7e5f, #feb47b); 
    color: #fff;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    height: 100vh;
    text-align: center;
  }
  
  h1 {
    font-size: 3rem;
    font-weight: bold;
    letter-spacing: 1.5px;
    text-shadow: 2px 2px 8px rgba(0, 0, 0, 0.2);
    padding: 20px;
    border-radius: 10px;
    background: rgba(0, 0, 0, 0.5);
    box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.2);
    margin-bottom: 20px; 
  }
  
  .search-bar {
    width: 280px;
    padding: 12px 16px;
    font-size: 1.1rem;
    border-radius: 50px; 
    border: 2px solid #ddd; 
    background: rgba(255, 255, 255, 0.9);
    color: #333;
    outline: none;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
    transition: box-shadow 0.3s ease, border-color 0.3s ease;
  }
  
  .search-bar:focus {
    animation: pulseShadow 1.5s infinite ease-in-out; 
    border-color: #ff7e5f; 
  }
  
  @keyframes pulseShadow {
    0% {
      box-shadow: 0 0 0 0 rgba(255, 255, 0, 0.4);
    }
    50% {
      box-shadow: 0 0 15px 5px rgba(255, 255, 0, 0.8); 
    }
    100% {
      box-shadow: 0 0 0 0 rgba(255, 255, 0, 0.4); 
    }
  }
  </style>
  
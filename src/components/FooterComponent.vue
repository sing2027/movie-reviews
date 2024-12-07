<template>
    <footer class="footer bg-dark text-center text-white py-3">
      <p class="mb-0">&copy; {{ new Date().getFullYear() }} Movie Reviews. All rights reserved.</p>
    </footer>
  </template>
  
  <style scoped>
  .footer {
    font-family: 'Arial', sans-serif;
    font-size: 0.9rem;
    background: linear-gradient(135deg, #043C51, #043C51); 
    color: #f8f9fa;
    box-shadow: 0px -2px 5px rgba(0, 0, 0, 0.2);
  }
  
  .footer p {
    margin: 0;
  }
  </style>
  
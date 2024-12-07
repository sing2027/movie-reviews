<template>
    <div class="review-card">
      <h2>{{ review.title }}</h2>
      <p>Rating: {{ review.rating }}/10</p>
      <p>{{ review.opinion }}</p>
      <p><small>Watched on: {{ review.watchDate }}</small></p>
    </div>
  </template>
  
  <script>
  export default {
    name: 'ReviewCard',
    props: {
      review: Object,
    },
  };
  </script>
  
  <style scoped>
  .review-card {
    border: 1px solid #ccc;
    padding: 15px;
    margin: 10px 0;
    border-radius: 5px;
  }
  </style>
  
<template>
  <div class="container review-container">
    <div v-if="review" class="card review-card mx-auto">
      <div class="card-body">
        <h1 class="card-title review-title">{{ review.title }}</h1>
        <p class="card-text review-rating">
          <strong>Rating:</strong>
          <span class="rating-number">{{ review.rating }}/10</span>
        </p>
        <p class="card-text review-opinion">{{ review.opinion }}</p>
        <p class="card-text review-watch-date">
          <strong>Watched on:</strong> {{ review.watchDate }}
        </p>
      </div>
    </div>
    <div v-else class="loading-container">
      <div class="loading-bar">
        <div class="loading-fill"></div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      review: null,
    };
  },
  created() {
    this.fetchReview();
  },
  methods: {
    async fetchReview() {
      try {
        const documentId = this.$route.params.documentId;
        const response = await axios.get(
          `https://mtm6407-headless-backend.onrender.com/api/reviews/${documentId}`
        );
        this.review = response.data.data;
      } catch (error) {
        console.error("Failed to fetch review:", error);
      }
    },
  },
};
</script>

<style scoped>
.review-container {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 50vh;
  padding: 15px;
  color: #212529;
  
}

.review-card {
  max-width: 600px;
  width: 100%;
  border-radius: 15px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.15);
  background: #ffffff;
  overflow: hidden;
  animation: fadeIn 1.5s ease-out;
}

.review-title {
  font-size: 2.5rem;
  font-weight: bold;
  color: #ffffff;
  text-align: center;
  animation: pulseGlow 2s infinite;
  background: #212529;
}

@keyframes pulseGlow {
  0% {
    text-shadow: 0 0 5px #ff5733, 0 0 10px #ff5733, 0 0 20px #ff5733;
  }
  50% {
    text-shadow: 0 0 10px #ff5733, 0 0 20px #ff5733, 0 0 40px #ff5733;
  }
  100% {
    text-shadow: 0 0 5px #ff5733, 0 0 10px #ff5733, 0 0 20px #ff5733;
  }
}

.review-rating {
  font-size: 1.2rem;
  margin-top: 10px;
  text-align: center;
}

.rating-number {
  font-size: 1.5rem;
  font-weight: bold;
  color: #ff5733;
}

.review-opinion {
  font-size: 1rem;
  margin: 15px 0;
  line-height: 1.6;
}

.review-watch-date {
  font-size: 0.9rem;
  font-style: italic;
  color: #6c757d;
}

.loading-container {
  text-align: center;
}

.loading-bar {
  position: relative;
  width: 200px;
  height: 10px;
  background-color: #dee2e6;
  border-radius: 5px;
  overflow: hidden;
  margin: 10px auto;
}

.loading-fill {
  position: absolute;
  width: 0%;
  height: 100%;
  background-color: #ff5c8d;
  animation: loadingAnimation 2s infinite;
  border-radius: 5px;
}

@keyframes loadingAnimation {
  0% {
    width: 0%;
  }
  50% {
    width: 50%;
  }
  100% {
    width: 100%;
  }
}

@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
</style>

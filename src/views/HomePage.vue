<template>
  <div class="container my-5 mt-4">
    <h1 class="text-center mb-4 animated titleEntrance">Movie Reviews</h1>
    <div class="mb-4 mt-4">
      <SearchBar @search="filterReviews" />
    </div>
    <div v-if="loading" class="loading-container">
      <div class="loading-bar">
        <div class="loading-fill"></div>
      </div>
    </div>
    <div v-else-if="filteredReviews.length" class="row g-4">
      <div v-for="review in filteredReviews" :key="review.documentId" class="col-lg-4 col-md-6">
        <div class="card h-100 shadow-sm animated cardEntrance">
          <div class="card-body d-flex flex-column">
            <h5 class="card-title">{{ review.title }}</h5>
            <router-link :to="`/review/${review.documentId}`" class="btn btn-outline-primary mt-auto animated btnFadeIn delay-1s">
              Read More
            </router-link>
          </div>
        </div>
      </div>
    </div>
    <p v-else class="text-center text-white">No reviews found.</p>
  </div>
</template>

<script>
import axios from "axios";
import SearchBar from "../components/SearchBar.vue";

export default {
  components: { SearchBar },
  data() {
    return {
      reviews: [],
      filteredReviews: [],
      loading: true,
    };
  },
  created() {
    this.fetchReviews();
  },
  methods: {
    async fetchReviews() {
      try {
        const response = await axios.get(
          "https://mtm6407-headless-backend.onrender.com/api/reviews"
        );
        this.reviews = response.data.data;
        this.filteredReviews = this.reviews;
      } catch (error) {
        console.error("Failed to fetch reviews:", error);
      } finally {
        this.loading = false;
      }
    },
    filterReviews(query) {
      this.filteredReviews = this.reviews.filter((review) =>
        review.title.toLowerCase().includes(query.toLowerCase())
      );
    },
  },
};
</script>

<style scoped>
.my-5 {
  padding: 20px;
}

.loading-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  min-height: 200px;
}

.text-center {
  text-align: center;
}

.text-muted {
  color: #ffffff;
  font-size: 1.2rem;
  font-style: italic;
  margin-top: 20px;
  animation: fadeIn 1.5s ease-out;
}

@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

.loading-bar {
  position: relative;
  width: 200px;
  height: 10px;
  background-color: rgba(0, 0, 0, 0.1);
  border-radius: 5px;
  overflow: hidden;
  margin-bottom: 10px;
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

.card {
  transition: transform 0.3s ease, box-shadow 0.3s ease, opacity 0.3s ease;
  animation: cardEntrance 1.5s ease-out;
  border-radius: 15px;
  background: #ffffff;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  margin-bottom: 30px;
  transform-style: preserve-3d;
}

.card:hover {
  transform: rotateY(10deg) rotateX(5deg);
  box-shadow: 0 15px 30px rgba(0, 0, 0, 0.2);
}

.card-body {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  padding: 20px;
}

.card-title {
  font-size: 1.25rem;
  font-weight: 600;
  color: #000000;
  margin-bottom: 15px;
}

.btn:hover {
  background: linear-gradient(135deg, #043C51, #ffffff, #043C51);
  background-size: 200% 100%;
  background-position: right center;
  color: white;
  transform: translateY(-3px) scale(1.05);
  transition: background-position 0.5s ease-in-out, transform 0.3s ease-in-out;
}

.btn {
  background: linear-gradient(135deg, #ffffff, #043C51, #ffffff);
  background-size: 200% 100%;
  background-position: left center;
  opacity: 0;
  animation: btnFadeIn 1s ease-in-out forwards;
  animation-delay: 1s;
  padding: 10px 20px;
  border-radius: 25px;
  font-weight: 600;
  border: 2px solid #043C51;
  color: #ffffff;
  margin-top: 20px;
  transition: background-position 0.5s ease-in-out, transform 0.3s ease-in-out;
}

@keyframes fadeIn {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}

@keyframes cardEntrance {
  0% {
    transform: scale(0.8);
    opacity: 0;
  }
  100% {
    transform: scale(1);
    opacity: 1;
  }
}

@keyframes btnFadeIn {
  0% {
    opacity: 0;
    transform: translateY(15px);
  }
  100% {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>

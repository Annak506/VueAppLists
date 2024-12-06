<template>
  <li>
    <h3 @click="toggleDetails">{{ title }}</h3>
    <div v-if="showDetails" class="details-container">
      <p><strong>Materials:</strong> {{ materials }}</p>
      <p><strong>Instructions:</strong> {{ instruction }}</p>
    </div>
  </li>
</template>

<script>
export default {
  props: ['title', 'instruction', 'materials'],
  data() {
    return {
      showDetails: false,
    };
  },
  methods: {
    toggleDetails() {
      this.showDetails = !this.showDetails;
    },
  },
};
</script>

<style scoped>
li {
  background-color: #9caf88;
  color: white;
  padding: 1rem;
  margin: 1rem 0;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  transition: background-color 0.3s, transform 0.3s;
}
li:hover {
  background-color: #7a8f6d;
  transform: translateY(-2px);
}
li h3 {
  margin: 0;
  font-size: 1.2rem;
  font-weight: bold;
  cursor: pointer;
}
.details-container {
  margin-top: 0.5rem;
  background-color: #f9f9f9;
  padding: 1rem;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  color: #333;
}
.details-container p {
  margin: 0.5rem 0;
}
</style>

<template>
  <li>
    <h3 @click="toggleDetails">{{ title }}</h3>
    <div v-if="showDetails">
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
p {
  margin: 0.5rem 0 0;
  padding: 0.5rem;
  background-color: #fff;
  color: #333;
  border-radius: 4px;
}
div {
  margin-top: 0.5rem;
}
</style>

<template>
  <li>
    <h3>{{ title }}</h3>
  </li>
</template>

<script>
export default {
  props: ['title'],
};
</script>

<style scoped>
li {
  background-color: #9caf88; /* Sage green background */
  color: white;
  padding: 1rem;
  margin: 1rem 0;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  transition: background-color 0.3s, transform 0.3s;
}

li:hover {
  background-color: #7a8f6d; /* Slightly darker sage green on hover */
  transform: translateY(-2px);
}

li h3 {
  margin: 0;
  font-size: 1.2rem;
  font-weight: bold;
}
</style>

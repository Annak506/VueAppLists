<template>
  <li>
    <h3>{{ userName }}</h3>
    <button @click="viewProjects">View game ideas</button>
  </li>
</template>

<script>
export default {
  props: ['id', 'userName'],
  emits: ['list-projects'],
  methods: {
    viewProjects() {
      this.$emit('list-projects', this.id);
    },
  },
};
</script>

<style scoped>
li {
  margin: 0.5rem 0;
  padding: 1rem;
  background-color: #fff7e6; 
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  border: 2px solid #ffcc99; 
  border-radius: 10px;
  transition: transform 0.2s ease-in-out, box-shadow 0.2s ease-in-out;
}

li:hover {
  transform: translateY(-5px);
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.15);
}

li h3 {
  margin: 0;
  color: #ff9966; 
  font-size: 1.2rem;
  font-weight: bold;
}

button {
  background-color: #ff9966; 
  color: white;
  padding: 0.5rem 1rem;
  border: none;
  border-radius: 25px;
  font-size: 1rem;
  cursor: pointer;
  transition: background-color 0.3s;
}

button:hover {
  background-color: #ff704d; 
}
</style>

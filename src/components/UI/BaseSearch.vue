<template>
  <form>
    <input type="search" @input="search" :value="searchTerm" placeholder="How many months old is your baby?" />
  </form>
</template>

<script>
export default {
  props: ['searchTerm'],
  emits: ['search'],
  methods: {
    search(event) {
      this.$emit('search', event.target.value);
    },
  },
};
</script>

<style scoped>
input {
  font: inherit;
  width: 100%;
  display: block;
  padding: 0.75rem;
  border: 2px solid #ffcc99; 
  border-radius: 8px; 
  font-size: 1.1rem;
  background-color: #fff; 
  transition: border-color 0.3s, background-color 0.3s;
  margin-bottom: 1rem;
}

input:focus {
  outline: none;
  border-color: #ff9966; 
  background-color: #ffe0cc; 
}

input::placeholder {
  color: #aaa; 
}
</style>

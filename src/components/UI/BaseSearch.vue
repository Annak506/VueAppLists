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
  border: 2px solid #ffcc99; /* Soft peach border */
  border-radius: 8px; /* Rounded corners */
  font-size: 1.1rem;
  background-color: #fff; /* White background */
  transition: border-color 0.3s, background-color 0.3s;
  margin-bottom: 1rem;
}

input:focus {
  outline: none;
  border-color: #ff9966; /* Darker peach when focused */
  background-color: #ffe0cc; /* Light peach background when focused */
}

input::placeholder {
  color: #aaa; /* Subtle placeholder text */
}
</style>

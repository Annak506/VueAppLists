<template>
  <section>
    <slot></slot>
  </section>
</template>

<style scoped>
section {
  margin: 2rem;
  border: 2px solid #ffcc99; 
  padding: 1.5rem;
  background-color: #fff3e6; 
  border-radius: 12px; 
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1); 
  flex: 1;
}

section:hover {
  border-color: #ff9966; 
}

slot {
  font-size: 1.1rem;
  color: #333;
}
</style>

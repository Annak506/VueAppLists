<template>
  <section>
    <slot></slot>
  </section>
</template>

<style scoped>
section {
  margin: 2rem;
  border: 2px solid #ffcc99; /* Soft peach border */
  padding: 1.5rem;
  background-color: #fff3e6; /* Light peach background */
  border-radius: 12px; /* Rounded corners */
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1); /* Light shadow */
  flex: 1;
}

section:hover {
  border-color: #ff9966; /* Darker peach when hovered */
}

slot {
  font-size: 1.1rem;
  color: #333;
}
</style>

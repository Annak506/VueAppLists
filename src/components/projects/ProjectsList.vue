<template>
  <base-container v-if="user">
    <h2>Playtime for a {{ user.fullName }} old</h2>
    <ul v-if="hasProjects">
      <project-item v-for="prj in user.projects" :key="prj.id" :title="prj.title" />
    </ul>
    <h3 v-else>No projects found.</h3>
  </base-container>

  <base-container v-else>
    <h3>Please select a month to see the game ideas for that age.</h3>
  </base-container>
</template>

<script>
import ProjectItem from './ProjectItem.vue';
import { computed } from 'vue';

export default {
  components: {
    ProjectItem,
  },
  props: ['user'],
  setup(props) {
    const hasProjects = computed(() => {
      return props.user && props.user.projects && props.user.projects.length > 0;
    });

    return {
      hasProjects,
    };
  },
};
</script>

<style scoped>
base-container {
  background-color: #e3e9d4; 
  border: 2px solid #a7b89b; 
  padding: 1.5rem;
  border-radius: 12px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  margin-bottom: 1.5rem;
}

h2 {
  color: #8fa78f; 
  font-size: 1.5rem;
  margin-bottom: 1rem;
}

h3 {
  color: #ff9966;
  font-size: 1.1rem;
  text-align: center;
}

ul {
  list-style: none;
  margin: 0;
  padding: 0;
}

ul li {
  margin: 0.5rem 0;
}
</style>

<template>
  <base-container v-if="user">
    <h2>{{ user.fullName }}: Projects</h2>
    <ul v-if="hasProjects">
      <project-item v-for="prj in user.projects" :key="prj.id" :title="prj.title"></project-item>
    </ul>
    <h3 v-else>No projects found.</h3>
  </base-container>
  <base-container v-else>
    <h3>No user selected.</h3>
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
      return props.user.projects && props.user.projects.length > 0;
    });

    return {
      hasProjects,
    };
  },
};
</script>

<style scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
}
</style>

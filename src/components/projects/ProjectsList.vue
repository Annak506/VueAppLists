<template>
  <base-container v-if="user">
    <h2>Playtime for a {{ user.fullName }} old</h2>
    <ul v-if="hasProjects">
      <project-item
        v-for="prj in user.projects"
        :key="prj.id"
        :title="prj.title"
        :instruction="prj.instruction"
        :materials="prj.materials"
      />
    </ul>
    <h3 v-else>No game ideas found.</h3>
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

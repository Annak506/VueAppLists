<template>
  <base-container>
    <h2>Play ideas per month</h2>
    <base-search @search="updateSearch" :search-term="enteredSearchTerm"></base-search>
    <div>
      <button @click="sort('asc')" :class="{selected: sorting === 'asc'}">Sort Ascending</button>
      <button @click="sort('desc')" :class="{selected: sorting === 'desc'}">Sort Descending</button>
    </div>
    <ul>
      <user-item
        v-for="user in displayedUsers"
        :key="user.id"
        :user-name="user.fullName"
        :id="user.id"
        @list-projects="$emit('list-projects', $event)"
      ></user-item>
    </ul>
  </base-container>
</template>

<script>
import UserItem from './UserItem.vue';
import { ref, computed, watch } from 'vue';

export default {
  components: {
    UserItem,
  },
  props: ['users'],
  emits: ['list-projects'],
  setup(props) {
    // Search logic
    const enteredSearchTerm = ref('');
    const activeSearchTerm = ref('');

    watch(enteredSearchTerm, function (newValue) {
      setTimeout(() => {
        if (newValue === enteredSearchTerm.value) {
          activeSearchTerm.value = newValue;
        }
      }, 300);
    });

    const availableUsers = computed(() => {
      if (activeSearchTerm.value) {
        return props.users.filter((usr) =>
          usr.fullName.toLowerCase().includes(activeSearchTerm.value.toLowerCase())
        );
      }
      return props.users || [];
    });

    // Sorting logic by ID (ascending or descending)
    const sorting = ref(null);

    const displayedUsers = computed(() => {
      if (!sorting.value) {
        return availableUsers.value;
      }
      return availableUsers.value.slice().sort((u1, u2) => {
        if (sorting.value === 'asc') {
          return u1.id.localeCompare(u2.id); // Ascending order by ID
        } else if (sorting.value === 'desc') {
          return u2.id.localeCompare(u1.id); // Descending order by ID
        }
        return 0;
      });
    });

    function sort(mode) {
      sorting.value = mode;
    }

    function updateSearch(val) {
      enteredSearchTerm.value = val;
    }

    return {
      enteredSearchTerm,
      updateSearch,
      displayedUsers,
      sorting,
      sort,
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

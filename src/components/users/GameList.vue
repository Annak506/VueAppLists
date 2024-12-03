<template>
  <base-container>
    <h2>Play ideas per month</h2>
    <base-search @search="updateSearch" :search-term="enteredSearchTerm"></base-search>
    <div>
      <button @click="sort('asc')" :class="{selected: sorting === 'asc'}">Sort Ascending</button>
      <button @click="sort('desc')" :class="{selected: sorting === 'desc'}">Sort Descending</button>
    </div>
    <ul>
      <game-item
        v-for="user in displayedUsers"
        :key="user.id"
        :user-name="user.fullName"
        :id="user.id"
        @list-projects="$emit('list-projects', $event)"
      ></game-item>
    </ul>
  </base-container>
</template>

<script>
import GameItem from './GameItem.vue';
import { ref, computed, watch } from 'vue';

export default {
  components: {
    GameItem,
  },
  props: ['users'],
  emits: ['list-projects'],
  setup(props) {
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

    const sorting = ref(null);

    const displayedUsers = computed(() => {
      if (!sorting.value) {
        return availableUsers.value;
      }
      return availableUsers.value.slice().sort((u1, u2) => {
        if (sorting.value === 'asc') {
          return u1.id.localeCompare(u2.id);
        } else if (sorting.value === 'desc') {
          return u2.id.localeCompare(u1.id);
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

button {
  background-color: #ff9966; 
  color: white;
  padding: 0.5rem 1.5rem;
  border: none;
  border-radius: 25px;
  margin: 0.2rem 0.5rem;
  font-size: 1rem;
  cursor: pointer;
  transition: background-color 0.3s;
}

button:hover {
  background-color: #ff704d; 
}

.selected {
  background-color: #ff704d; 
}

base-container {
  background-color: #fff7e6; 
  border: 2px solid #ffcc99; 
  padding: 1.5rem;
  border-radius: 12px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  margin-bottom: 1.5rem;
}

h2 {
  color: #ff9966; 
  font-size: 1.5rem;
  margin-bottom: 1rem;
}

h3 {
  color: #666;
  font-size: 1.1rem;
  text-align: center;
}
</style>

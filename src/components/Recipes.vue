
  
  <script>
  import { ref, onMounted } from 'vue';
  import { readDB } from '../../firebaseconfig.js';
  import Recipe from './Recipe.vue';

  export default {
    components: {
    Recipe
    },
    setup() {
      const dbData = ref([]);
      const loading = ref(true);
  
      const fetchData = async () => {
  try {
    const rawData = await readDB();
    // Check if rawData is not null or undefined before proceeding
    if (rawData) {
      // Transform the object into an array of objects
      dbData.value = Object.entries(rawData).map(([id, data]) => ({
        id,
        ...data
      }));
    } else {
      // Handle the case where rawData is null or undefined
      console.log('No data returned from readDB');
      dbData.value = []; // Set dbData to an empty array or a default value
    }
  } catch (error) {
    console.error('Failed to fetch data:', error);
  } finally {
    loading.value = false;
  }
};

    onMounted(() => {
      fetchData();
    });

    return { dbData, loading };
  },
  };
  </script>
<template>
  <div>
    <h1>Database Content</h1>
    <div v-if="loading">Loading...</div>
    <div v-else>
      <ul>
        <li v-for="(item, index) in dbData" :key="index">
          <!-- Use the Recipe component for each item -->
            {{ index + 1 }}
          <Recipe :recipe="item" />
        </li>
      </ul>
    </div>
  </div>
</template>

  <style>
  /* Add styles here */
  </style>
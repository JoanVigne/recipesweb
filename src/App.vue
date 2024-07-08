<script setup>
import { ref } from 'vue';
import FormAddRecipe from "./components/FormAddRecipe.vue"
import Recipes from "./components/Recipes.vue"


const showModal = ref(false);
const toggleModal = () => {
  showModal.value = !showModal.value;
};
</script>

<template>
  <header>
    <button @click="toggleModal">Add Recipe</button>
  </header>
  <aside>
    <div v-if="showModal" class="modal-overlay" @click="toggleModal">
      <div class="modal-content" @click.stop>
        <FormAddRecipe />
        <button @click="toggleModal">Close</button>
      </div>
    </div>
  </aside>
  <main>
    <Recipes />
  </main>
</template>

<style scoped>
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
}

.modal-content {
  background: white;
  padding: 20px;
  border-radius: 8px;
  position: relative;
}
</style>

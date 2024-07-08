<template>
    <div>
      <form @submit.prevent="submitForm">
        <div>
          <label for="name">Recipe Name:</label>
          <input type="text" id="name" v-model="recipe.name" required>
        </div>
        <div>
          <label for="ingredients">Ingredients:</label>
          <textarea id="ingredients" v-model="recipe.ingredients" required></textarea>
        </div>
        <div>
          <label for="instructions">Instructions:</label>
          <textarea id="instructions" v-model="recipe.instructions" required></textarea>
        </div>
        <button type="submit">Submit</button>
      </form>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        recipe: {
          name: '',
          ingredients: '',
          instructions: ''
        }
      };
    },
    methods: {
      submitForm() {
        console.log('Submitted recipe:', this.recipe);
        // Here you would typically send this data to a server or handle it according to your needs
      }
    }
  };
  </script>
  
  <style>
  form {
    max-width: 600px;
    margin: 20px auto;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 8px;
    background-color: #f9f9f9;
    color: black;
  }
  
  div {
    margin-bottom: 10px;
  }
  
  label {
    display: block;
    margin-bottom: 5px;
    font-weight: bold;
  }
  
  input[type="text"],
  textarea {
    width: 100%;
    padding: 8px;
    margin: 5px 0 5px 0;
    display: inline-block;
    border: 1px solid #ccc;
    border-radius: 4px;
    box-sizing: border-box;
    resize: vertical; 
  }
  
  button[type="submit"] {
    width: 100%;
    background-color: #4CAF50;
    color: white;
    padding: 14px 20px;
    margin: 8px 0;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }
  
  button[type="submit"]:hover {
    background-color: #45a049;
  }
  </style>
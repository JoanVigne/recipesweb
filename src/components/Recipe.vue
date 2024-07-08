
  
  <script>
  export default {
    props: {
      recipe: Object
    }
  };
  </script>

  <template>
    <div class="recipe">
      <strong>Document ID:</strong> {{ recipe.id }}<br>
      <strong>Name:</strong> {{ recipe.name }}
      <!-- Add more properties as needed -->
    </div>
  </template>
  
  <style>
  /* Style your recipe component */
  .recipe {
    margin-bottom: 10px;
  }
  </style>
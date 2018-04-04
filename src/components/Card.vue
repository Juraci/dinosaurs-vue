<template>
  <div class="card">
    <header>{{ title }}</header>
    <div class="content">
      {{ content }}
    </div>
  </div>
</template>

<script>
  export default {
    name: 'Card',
    data: function() {
      return {
        title: 'Dinosaurs',
        content: "Dinonyco",
      };
    },
  }
</script>

<style scoped>
  div.card {
    text-align: left;
    margin: 5rem;
    border: 2px solid Gray;
    border-radius: 10px;
  }

  header {
    border-radius: 8px 8px 0 0;
    background: orange;
    font-size: 1.5em;
    color: white;
    padding: 1rem;
  }

  .content {
    padding: 1rem;
  }
</style>

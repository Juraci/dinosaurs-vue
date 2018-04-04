<template>
  <div class="card">
    <header>{{ title }}</header>
    <div class="dino-form">
      <input id="itemForm" v-on:keypress.enter="addItem"/>
      <button type="button" name="add dinosaur" v-on:click="addItem">Add Dinossaur</button>
    </div>
    <ul>
      <li v-bind:key="item.id" v-for="item in items">
        {{ item.text }}
      </li>
    </ul>
  </div>
</template>

<script>
  export default {
    name: 'Card',
    data: function() {
      return {
        title: 'Dinosaurs',
        items: [
          { id: 1, text: "Velociraptor" },
          { id: 2, text: "Triceratops" },
          { id: 3, text: "Stegosaurus" },
        ],
      };
    },
    methods: {
      addItem: function() {
        const input = document.getElementById('itemForm');

        if(input.value !== "" && input.value !== " ") {
          this.items.push({ id: this.items.length + 1, text: input.value });
        }

        input.value = "";
      }
    }
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

  .dino-form {
    margin-left: 1rem;
    margin-top: 1rem;
  }

  input {
    margin-right: 5px;
  }

  ul {
    margin-left: 0px;
    -webkit-margin-before: 1em;
    -webkit-margin-after: 1em;
    -webkit-margin-start: 0px;
    -webkit-margin-end: 0px;
    -webkit-padding-start: 1rem;
  }

  li {
    list-style-type: none;
    border: 1px solid Gray;
    margin-right: 1rem;
    margin-top: 2px;
    padding: 0.3rem;
    border-radius: 8px;
  }
</style>

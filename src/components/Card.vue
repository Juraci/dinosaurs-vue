<template>
  <div class="card">
    <header>{{ title | capitalize }}</header>
    <div class="dino-form">
      <input id="itemForm" v-on:keypress.enter="addItem"/>
      <button type="button" name="add dinosaur" v-on:click="addItem">Add Dinossaur</button>
    </div>
    <ul>
      <li v-bind:key="item.id" v-for="item in items">
        <button class="removeItem" v-on:click="removeItem(item.id)" type="button" name="button">x</button>
        <h4 class="dinoName">{{ item.text | capitalize }}</h4>
        <span v-if="item.weight" class="basicInfo">The {{ item.text | capitalize }} weighs {{ item.weight }}.</span>
        <a class="link" v-bind:href="item.text | undercase | url">{{ item.text | undercase | url }}</a>
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
          {
            id: 1,
            text: "Velociraptor",
            weight: "15 kg",
          },
          {
            id: 2,
            text: "Triceratops",
            weight: "6000 kg",
          },
          {
            id: 3,
            text: "stegosaurus",
            weight: "2500 kg",
          },
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
      },
      removeItem: function(itemId) {
        const itemToRemove = this.items.find(i => i.id === itemId);
        const index = this.items.indexOf(itemToRemove);
        this.items.splice(index, 1);
      }
    },
    filters: {
      capitalize: function(value) {
        if(!value) return '';
        value = value.toString();
        return value.charAt(0).toUpperCase() + value.slice(1);
      },
      undercase: function(value) {
        if(!value) return '';
        value = value.toString();
        return value.toLowerCase();
      },
      url: function(value) {
        if(!value) return '';
        return `https://pt.wikipedia.org/wiki/${value}`;
      },
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
    border-radius: 5px;
  }

  .removeItem {
    border-radius: 10px;
    border: 1px solid Orange;
    font-size: 1rem;
    background-color: orange;
    color: white;
  }

  .dinoName {
    display: inline;
    margin-left: 0.5rem;
  }

  .basicInfo {
    display: block;
    font-size: 1em;
    margin-top: 0.3rem;
    margin-left: 1.9rem;
  }

  .link {
    font-size: 0.8em;
    margin-top: 0.3rem;
    margin-left: 1.9rem;
    display: block;
  }
</style>

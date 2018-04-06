<template>
  <div id="app">
    <Card
      v-bind:items="items"
      v-on:add="addItem"
      v-on:remove="removeItem"
    />
  </div>
</template>

<script>
import Card from './components/Card.vue'

export default {
  name: 'app',
  data: function() {
    return {
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
    }
  },
  methods: {
    addItem: function(value) {
      if(value !== "" && value !== " ") {
        this.items.push({ id: this.items.length + 1, text: value });
      }
    },
    removeItem: function(itemId) {
      const itemToRemove = this.items.find(i => i.id === itemId);
      const index = this.items.indexOf(itemToRemove);
      this.items.splice(index, 1);
    }
  },
  components: {
    Card,
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

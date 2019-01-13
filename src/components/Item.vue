<template>
  <div class="item" v-bind:class="{'checked': item.completed}">
    <p>
      <input type="checkbox" v-on:change="toggleChecked">
      {{item.title}}
      <button v-on:click="$emit('delete-item', item.id)" class="delete">X</button>
    </p>
  </div>
</template>

<script>
export default {
  name: "Item",
  props: ["item"],
  methods: {
    toggleChecked() {
      this.item.completed = !this.item.completed;
    }
  }
};
</script>

<style scoped>
p,
.item {
  background-color: #35495e;
  font-size: 1rem;
}
.item {
  /* background-color: #2c3e50; */
  color: white;
  padding: 10px;
  border-bottom: 1px #42b883 solid;
}

.checked {
  text-decoration: line-through;
  color: #42b883;
}

.delete {
  background: #ff0000;
  color: white;
  border: none;
  padding: 5px 9px;
  border-radius: 50%;
  cursor: pointer;
  float: right;
}
</style>

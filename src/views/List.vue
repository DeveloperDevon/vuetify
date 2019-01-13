<template >
  <div class="list">
    <ListHeader/>
    <AddItem v-on:add-item="addItem"/>
    <div v-bind:key="item.id" v-for="item in list">
      <h3>
        <Item v-bind:item="item" v-on:delete-item="deleteItem"/>
      </h3>
    </div>
  </div>
</template>

<script>
import Item from "../components/Item.vue";
import ListHeader from "../components/layout/ListHeader";
import AddItem from "../components/AddItem.vue";
import axios from "axios";
export default {
  name: "List",
  components: {
    Item,
    ListHeader,
    AddItem
  },
  data() {
    return {
      list: []
    };
  },
  methods: {
    addItem(newItem) {
      const { title, completed } = newItem;
      axios
        .post("https://jsonplaceholder.typicode.com/todos", {
          title,
          completed: false
        })
        .then(res => (this.list = [...this.list, res.data]))
        .catch(err => console.log(err));
    },
    deleteItem(id) {
      axios
        .delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
        .then(res => (this.list = this.list.filter(item => item.id !== id)))
        .catch(err => console.log(err));
    }
  },
  created() {
    axios
      .get("https://jsonplaceholder.typicode.com/todos?_limit=15")
      .then(res => (this.list = res.data))
      .catch(err => console.log(err));
  }
};
</script>

<style scoped>
h1 {
  color: #42b883;
  background-color: #1d2935;
}

.list {
  width: 80%;
  margin: 20px 0 0 10%;
  border: 2px #42b883 solid;
  border-radius: 3px;
}
</style>


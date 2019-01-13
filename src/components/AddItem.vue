<template>
  <div>
    <form v-on:submit="addItem">
      <input type="text" v-model="title" name="title" placeholder="Add Item...">
      <span>
        <input type="submit" value="+" class="add-btn">
      </span>
    </form>
  </div>
</template>

<script>
export default {
  name: "AddItem",
  data() {
    return {
      title: ""
    };
  },
  methods: {
    addItem(e) {
      e.preventDefault();
      const newItem = {
        title: this.title,
        checked: false
      };
      //Send to parent
      this.$emit("add-item", newItem);

      this.title = "";
    }
  }
};
</script>

<style scoped>
form {
  display: flex;
}
input {
  background-color: #efefef;
}
input[type="text"] {
  flex: 10;
  padding: 5px;
}
input[type="submit"] {
  flex: 2;
}
.add-btn {
  background: #42b883;
  color: white;
  border: none;
  padding: 5px 9px;
  margin: 0 10px 0 10px;
  border-radius: 50%;
  cursor: pointer;
  float: right;
}
span {
  background-color: #35495e;
  border-bottom: 1px #42b883 solid;
}
</style>

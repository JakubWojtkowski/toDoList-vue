<template>
  <div class="item">
    <input type="text" placeholder="item" v-model="newItem" />
    <button @click="addItem">Add item</button>
  </div>

  <ToDoItem
    v-for="item in items"
    :key="item.id"
    :item="item"
    @clickedId="removeItem"
  />
</template>

<script>
import ToDoItem from "./ToDoItem.vue";
export default {
  components: { ToDoItem },
  data() {
    return {
      newItem: "",
      items: [
        { id: 1, title: "Shopping", completed: false },
        { id: 2, title: "Coding", completed: false },
      ],
    };
  },
  methods: {
    addItem() {
      this.items.push({
        id: Math.random(),
        title: this.newItem,
        completed: false,
      });
      this.newItem = "";
    },

    removeItem(id) {
      const index = this.items.findIndex((el) => el.id === id);
      this.items[index].completed = true;
    },
  },
};
</script>

<style>
.item {
  border: 1px solid #cdcdcd;
  margin: 8px;
  padding: 10px;
}

.completed {
  opacity: 0.5;
}

.completed h2 {
  text-decoration: line-through;
}
</style>

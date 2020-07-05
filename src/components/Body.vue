<template>
  <div>
    <ul>
      <li v-for="(todo,key) in todos" :key="key">
        <input type="checkbox" v-model="todo.isDone" />
        <span :class="{done: todo.isDone}">{{todo.title}}</span>
        <span @click="deleteItem(key)" class="command">[x]</span>
      </li>
      <li v-show="!todos.length">タスクが無いニャ</li>
    </ul>
    <form @submit.prevent="addItem">
      <input type="text" v-model="newItem" />
      <input type="submit" value="追加" />
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newItem: "",
      todos: []
    };
  },
  watch: {
    todos: {
      handler: function() {
        localStorage.setItem("todos", JSON.stringify(this.todos));
      },
      deep: true
    }
  },
  mounted: function() {
    this.todos = JSON.parse(localStorage.getItem("todos")) || [];
  },
  methods: {
    addItem: function() {
      var item = {
        title: this.newItem + "🐈",
        isDone: false
      };
      this.todos.push(item);
      this.newItem = "";
    },
    deleteItem: function(key) {
      if (confirm("本当に削除するかにゃ？")) this.todos.splice(key, 1);
    }
  }
};
</script>

<style scoped>
li {
  line-height: 2;
}

input[type="text"] {
  padding: 2px;
}

.command {
  font-size: 12px;
  cursor: pointer;
  color: #08c;
}

ul {
  padding: 0;
  list-style: none;
}

li > span.done {
  text-decoration: line-through;
  color: #bbb;
}
</style>
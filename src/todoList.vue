<template>
  <div id="app">
    <h2>ToDo List</h2>
    <input
      id="add-input"
      v-model="todoText"
      @keyup.enter="addTodo"
      placeholder="Escreva aqui!"
    />
    <ul>
      <todo
        v-for="(todoItem, index) in todoList"
        :todoItem="todoItem"
        :index="index"
      ></todo>
    </ul>
  </div>
</template>

<script>
import Todo from "./components/todo";
export default {
  name: "todoList",
  components: {
    Todo,
  },
  data() {
    return {
      todoText: "",
    };
  },
  computed: {
    todoList() {
      return this.$store.getters.todos;
    },
  },
  methods: {
    addTodo() {
      this.$store.commit("addTodo", this.todoText);
      this.todoText = "";
    },
    deleteTodo(index) {
      this.$store.commit("deleteTodo", index);
    },
  },
};
</script>

<style>
body {
  font-family: Helvetica, sans-serif;
}
#app {
  width: 800px;
  margin: 30px auto;
}
#add-input {
  width: 750px;
  height: 35px;
  padding: 0 5px;
}
ul {
  list-style: none;
  padding: 0;
}

.rodape {
  text-align: center;
  font-family: var(--font-action);
  align-items: center;
  border-radius: 2px;
  background: white;
  display: flex;
  flex-direction: column;
  margin-top: 10px;
  padding: 2%;
}

.rodape h3 {
  text-align: center;
  align-items: center;
  font-size: 12px;
  font-size: 2rem;
  text-align: center;
  display: flex;
}
.icons ion-icon {
  text-align: center;
  align-items: center;
  color: green;
  margin-right: 5px;
  width: 35spx;
  height: 35px;
  font-size: 2rem;
}

.icons ion-icon:hover {
  font-size: 3rem;
  color: greenyellow;
}
</style>

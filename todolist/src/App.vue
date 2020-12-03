<template>
  <v-app id="app">
    <h1 style="display: flex; flex-wrap: wrap; justify-content: space-between">
      <div>ToDo</div>

      <div style="bakgroud-color: blue">
        <input
          style="background-color: #888888; margin-right: 10px"
          type="text"
          v-model="newTask"
          placeholder="blablabla"
          @keyup.enter="addNewTask"
        />
        <button @click="addNewTask">ADD</button>

        <!-- <v-btn
        color="white"
        outlined
        @click="addNewTask">Add</v-btn> -->
      </div>
    </h1>
    <div class="placeCard">
      <v-card
        max-width="600px"
        class="cards"
        v-for="(task, index) in list"
        :key="index"
        v-show="!task.done"
      >
        <v-checkbox v-model="task.done"></v-checkbox>
        <!-- <button @click="done(index)">change</button> -->
        <div class="undoneTask">
          {{ task.task }}
        </div>
        <v-icon @click="remove(index)">mdi-cancel</v-icon>
      </v-card>
    </div>

    <h1>Done</h1>
    <div class="placeCard">
      <v-card
        max-width="600px"
        class="cards"
        v-for="(task, index) in list"
        :key="index"
        v-show="task.done"
      >
        <v-checkbox v-model="task.done"></v-checkbox>
        <!-- <button @click="unDone(index)">change</button> -->
        <div class="doneTask">
          {{ task.task }}
        </div>

        <v-icon @click="remove(index)">mdi-cancel</v-icon>
      </v-card>
    </div>
  </v-app>
</template>

<script>
import HelloWorld from "./components/HelloWorld";

export default {
  name: "App",

  components: {
    HelloWorld,
  },
  data() {
    return {
      list: [
        {
          done: false,
          task: "aaaa",
        },

        {
          done: true,
          task: "bbbb",
        },

        {
          done: false,
          task: "cccc",
        },
      ],
    };
  },
  methods: {
    updateTitle(e) {
      this.title = e;
    },
    done(index) {
      return (this.list[index].done = true);
    },
    unDone(index) {
      return (this.list[index].done = false);
    },
    addNewTask() {
      this.list.unshift({
        done: false,
        task: this.newTask,
      }),
        (this.newTask = "");
    },
    remove(index) {
      this.list.splice(index, 1);
    },
  },
};
</script>

<style scoped>
#app {
  margin: auto;
}

.cards {
  padding: 0 10px;
  margin: 5px auto;
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
}
h1 {
  padding: 10px;
  background-color: black;
  color: white;
}
.doneTask {
  font-size: 30px;
  color: grey;
  text-decoration: line-through;
  width: 70%;
  margin: 10px;
}
.undoneTask {
  font-size: 30px;
  color: black;
  width: 70%;
  margin: 10px;
}
.placeCard {
  margin: 10px;
}
</style>

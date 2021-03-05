<template>
  <div class="container">
    <div class="task">
      <!-- title -->
      <div class="columns">
  <div class="column">
    Vendredi 05 mars 2021
  </div>
  <div class="column">
   VueJs Tutorial ToDo List
  </div>
  <div class="column">
        <span>Taches : {{ incomplete }}</span>
      </div>
</div>
      <!-- form -->
      <div class="form">
        <input
          type="text"
          placeholder="New Task"
          v-model="newTask"
          @keyup.enter="addTask"
        />
        <button @click="addTask"><i class="fas fa-plus-circle"></i></button>
      </div>
      <!-- task lists -->
      <div class="taskItems">
        <ul>
          <task-item
            v-bind:task="task"
            v-for="(task, index) in tasks"
            :key="task.id"
            @remove="removeTask(index)"
            @complete="completeTask(task)"
          ></task-item>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import TaskItem from "./todo-list";



export default {
  name: "todoCard",
  props: ['tasks'],
  components: {
    TaskItem,
  },
  data() {
    return {
      newTask: "",
    };
  },
  computed: {
    incomplete() {
      return this.tasks.filter(this.inProgress).length;
    },
  },
  methods: {
    addTask() {
      if (this.newTask) {
        this.tasks.push({
          title: this.newTask,
          completed: false,
        });
        this.newTask = "";
      }
    },
    inProgress(task) {
      return !this.isCompleted(task);
    },
    isCompleted(task) {
      return task.completed;
    },
    completeTask(task) {
      task.completed = !task.completed;
    },
    removeTask(index) {
      this.tasks.splice(index, 1);
    },
  },
};
</script>

<style>

body{font-family:poppins}

.columns{display: flex;
align-items: center;
justify-content: center;
justify-content: space-around;
box-shadow: 0px 5px 5px rgb(218, 210, 210);}

.columns .column {padding: 10px;
font-weight: 600;}

.task{
background-color: #fff;
border-radius : 8px;

}

input{border:none;
text-align: center;
font-size: 20px;
margin-top: 50px;
outline: none;
border-bottom: 3px solid rgba(119, 224, 219, 0.6);}

button{
  background-color: transparent;
  border: none;
}

.form{display: flex;
justify-content: center;
align-items:baseline;}

i{font-size: 50px;}

.fas{
  color: rgb(58, 195, 131);
  padding-left:  50px;
}
</style>
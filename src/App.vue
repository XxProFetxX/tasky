<template>
  <div id="app">
    <header-item></header-item>
    <task-list v-bind:tasks="tasks" v-on:delete-task="deleteTask"></task-list>
    <add-task v-on:add-task="addTask"></add-task>
    <footer-item></footer-item>
  </div>
</template>

<script>
  import TaskList from "./components/task-list.component.vue"
  import AddTask from "@/components/add-task.component.vue";
  import HeaderItem from "./components/common/header-item.component.vue"
  import FooterItem from "./components/common/footer-item.component.vue"
  export default {
    name: "App",
    components: {FooterItem, HeaderItem, AddTask, TaskList},
    data() {
      return {
        tasks: [
          { id: 1, title: "Prepare Final Project Status Report", completed: false},
          { id: 2, title: "Study English", completed: false},
          { id: 3, title: "Do Laundry", completed: false},
          { id: 4, title: "Cook breakfast", completed: false},
          { id: 5, title: "Learn Vue", completed: false},
        ]
      }
    },
    methods: {
      addTask(newTask) {
        this.tasks = [...this.tasks, newTask]
      },
      deleteTask(taskId) {
        this.tasks = this.tasks.filter(task => task.id !== taskId)
      }
    }
  }
</script>

<style>
  .containerXD {
    flex: 2;
  }
</style>
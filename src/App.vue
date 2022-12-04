<template>
  <div class="container">
    <Header @toggle-add-task="toggleAddTask" title="Task Tracker"/>
    <div v-show="showAddTask">
      <AddTask @add-task="addTask" />
    </div>
    <Tasks @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks" />
  </div>
</template>
<script>
import Header from "./components/Header.vue";
import Tasks from "./components/Tasks.vue";
import AddTask from "./components/AddTask.vue";
export default {
  name: 'App',
  components: {
    Header,
    Tasks,
    AddTask
  },
  data(){
    return{
      tasks: [],
      showAddTask : false,
    }
  },
  methods: {
    toggleAddTask(){
      this.showAddTask = !this.showAddTask
    },
    addTask(task){
      this.tasks = [...this.tasks, task]
    },
    deleteTask(id){
      if(confirm('Are you confirm')){
        this.tasks = this.tasks.filter((task)=> task.id !== id )
      }
    },
    toggleReminder(id){
      this.tasks = this.tasks.map((task) => task.id === id ? {...task, reminder: !task.reminder} : task )
    }
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: 'A Work',
        day: 'March 1st at 2:30px',
        reminder: true
      },
      {
        id: 2,
        text: 'B Work',
        day: 'March 2nd at 2:30px',
        reminder: true
      },
      {
        id: 3,
        text: 'C Work',
        day: 'March 3rd at 2:30px',
        reminder: true
      }
    ]
  },
}
</script>

<style>
.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  display: block;
  width: 100%;
}
</style>

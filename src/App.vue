<template>
    <div class="container">
      <Header @toggle-add-task="toggleAddTask"
      title="MEMO" 
      :showAddTask="showAddTask">
      </Header>
      <div v-show="showAddTask">
        <AddTask @add-task="addTask" />
      </div>
      <Tasks  @toggle-reminder="toggleReminder" 
              @delete-task="deleteTask" 
              :tasks="tasks" />
    </div>
</template>

<script>
import Header from './components/header.vue'
import Tasks from './components/Tasks.vue'
import AddTask from './components/AddTask.vue'

export default{
  name: 'App',
  components: {
    Header,
    Tasks,
    AddTask
  },
  data(){
    return {
      tasks:[],
      showAddTask: false
    }
  },
  methods:{
    toggleAddTask(){
      this.showAddTask = !this.showAddTask
    },
    addTask(task){
      this.tasks = [...this.tasks,task]
    },
     deleteTask(id){
      if(confirm('Are You Sure ?')){
        this.tasks = this.tasks.filter((task)=>task.id !== id)
      }
    },
    toggleReminder(id){
      this.tasks = this.tasks.map((task)=>
      task.id === id ? {...task,reminder: !task.reminder}:task)
    }
      

  },
  created(){
    this.tasks=[
      {
        id:1,
        text:'Doctors Appointment',
        day:'2023-03-27',
        time:'11:30',
        reminder:true,
      },
      {
        id:2,
        text:'Meeting at School',
        day:'2023-05-02',
        time:'10:00',
        reminder:true,
      },
      {
        id:3,
        text:'Food Shopping',
        day:'2023-10-17',
        time:'18:30',
        reminder:false,
      },
    ]
  }
}
</script>

<style>
        @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }
    body {
      font-family: 'Poppins', sans-serif;
    }
    .container {
      max-width: 500px;
      margin: 30px auto;
      overflow: auto;
      min-height: 300px;
      border: 1px solid steelblue;
      padding: 30px;
      border-radius: 5px;
    }
    .btn {
      display: inline-block;
      background: #000;
      color: #fff;
      border: none;
      padding: 10px 30px;
      margin: 10px;
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


<template>
  <div class="container">
    <Header title ="Task tracker" />
    <AddTask @add-task = addNewTask />
    <Tasks :tasks= "tasks" @delete-task = "deleteTask" @toggle-reminder = "toggleReminder" />
  </div>
</template>

<script>

import Header from './components/Header.vue';
import Tasks from './components/Tasks.vue';
import AddTask from './components/AddTask.vue';

  export default {
    name: "App",
    components: {
      Header,
      Tasks,
      AddTask,
    
    },

    methods: {
      deleteTask(id){
        if(confirm("Are you sure?")){
          this.tasks = this.tasks.filter(task => task.id !== id)
        }
      },

      addNewTask(task){
        this.tasks.push(task);
      },

      toggleReminder(id){
        this.tasks.forEach(element => {
          if(element.id === id){element.reminder = !element.reminder}
        });
      },

    
    },

    data(){
      return {
        tasks: [],
        showAddTask: false,
      }
    },

    created(){
      this.tasks = [
      {
            id: 1,
            text: "Doctor appointment",
            day: "March 1st at 2:30pm",
            reminder: true,
          },
          {
            id: 2,
            text: "Meeting at school",
            day: "March 3rd at 1:30pm",
            reminder: true,
          },
          {
            id: 3,
            text: "Food shopping",
            day: "March 15th at 11:30pm",
            reminder: false,
          },
      ]
    }

  }

</script>

<style >
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  font-family: "Poppins", sans-serif;
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

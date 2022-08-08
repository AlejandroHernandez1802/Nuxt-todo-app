<template>
  <div>
    <h1 class="title">Alejandro's to do app</h1>
    <h2 class="subtitle">Create a list of tasks</h2>

    <div class="task-adder">
      <input placeholder="Task to add..." type="text" class="task-input" v-model="userInput" @keypress.enter="handleTask"/>
      <button class="add-task-btn" @click="handleTask">ADD TASK</button>
    </div>

    <div class="tasks">
      <Task v-for="(task,index) in $store.state.tasks" :key="index" :task-content="task"/>
    </div>
  </div>
</template>

<script>

import Task from '../components/Task.vue';

export default {
  name: 'IndexPage',
  components:{
    Task
  },
  data(){
    return{
      userInput:'',
    }
  },
  methods:{
    handleTask(){
      if(this.userInput !== ''){
        this.$store.commit('ADD_TASK', this.userInput);
        this.userInput = '';
      }
      else{
        alert("You have to write something to add as a task!");
      }
    },
  }
}
</script>


<style>
  .title{
    font-family: 'Oleo Script Swash Caps', cursive;
    text-align: center;
    font-size: 5rem;
    color: white;
    margin-bottom: 0;
  }

  .subtitle{
    font-family: 'Urbanist', sans-serif;
    text-align: center;
    margin-top: 0;
  }

  .task-adder{
    width: 30%;
    margin: 100px auto;
    display: flex;
    justify-content: space-between;
  }

  .task-input{
    width: 80%;
    padding: 5px;
    background-color: transparent;
    color: white;
    font-family: 'Urbanist', sans-serif;
    font-size: 1.5rem;
    border: none;
    outline: none;
    border-bottom: solid 2px white;
  }

  .add-task-btn{
    border-radius: 5px;
    background-color: #59CE8F;
    font-family: 'Urbanist', sans-serif;
    color: white;
    font-weight: 700;
    cursor: pointer;
  }

  .tasks{
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }
</style>

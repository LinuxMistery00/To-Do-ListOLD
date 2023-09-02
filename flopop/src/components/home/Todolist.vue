<template>
    <div class="todolist">
      <div class="Inputs">
        <input id="Nome" type="text" v-model="nome" />
        <input id="Date" type="date" v-model="data" />
        <button @click="task" id="EnviarBTN">Enviar</button>
      </div>
      
      <div class="Tasks">
        <h2>Tarefas:</h2>
        <ul>
          <li v-for="(task, index) in tasks" :key="index">
            {{ task.nome }} - {{ task.data }}
          </li>
        </ul>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        nome: '',
        data: '',
        tasks: [],
      };
    },
    methods: {
      task() {
        const newTask = {
          nome: this.nome,
          data: this.data,
        };
        this.tasks.push(newTask);
        this.nome = '';
        this.data = '';
      },
    },
  };
  </script>
  
  <style scoped>
  .todolist {
  }
  
  #Nome,
  #Date {
    width: 25vh;
    height: 3vh;
    border: 0;
    border-radius: 3vh;
    background-color: #212223;
    color: #f1f2f3;
  }
  
  .Inputs {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    gap: 1vh;
  }
  
  #EnviarBTN {
    width: 25vh;
    border: 0;
    border-radius: 3vh;
    background-color: #212223;
    color: #f1f2f3;
    font-size: 3vh;
  }
  
  .Tasks {
    font-size: 5vh;
    text-align: center;
  }
  
  ul {
    list-style-type: none;
    padding: 0;
  }
  
  li {
    margin-bottom: 1vh;
  }
  </style>
  
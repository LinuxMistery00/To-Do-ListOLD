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
          <button @click="removeTask(index)" class="remove-button">Remover</button>
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
      tasks: JSON.parse(localStorage.getItem('tasks')) || [], // Carrega dados do localStorage
    };
  },
  watch: {
    // Use um watcher para monitorar mudanças na lista de tarefas e salvar no localStorage
    tasks: {
      handler(newTasks) {
        localStorage.setItem('tasks', JSON.stringify(newTasks));
      },
      deep: true, // Para detectar mudanças profundas no array
    },
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
    removeTask(index) {
      this.tasks.splice(index, 1);
    },
  },
};
</script>

<style scoped>
.todolist {
  /* Estilos da div principal */
  text-align: center;
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

#EnviarBTN,
.remove-button {
  width: 10vh; /* Tamanho ajustado para melhor aparência */
  border: 0;
  border-radius: 3vh;
  background-color: #212223;
  color: #f1f2f3;
  font-size: 2vh; /* Tamanho do botão ajustado */
  margin-left: 1vh; /* Espaçamento entre botões */
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
input:focus {   
  outline: none;
}
</style>

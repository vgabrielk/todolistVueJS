
<template>
  <div v-if="addedTask" class="success">
    <h5>Adicionado com sucesso</h5>
    <p><i class="fa-solid fa-check"></i></p>
  </div>
  <div class="tasks">
    <div class="row">
      <h1>Lista de tarefas</h1>
      <input
        placeholder="Escreva para adicionar uma nova tarefa!"
        maxlength="22"
        type="text"
        @keypress.enter="inputSubmit"
        v-model="currentTask"
      />
      <button @click="addTask">Adicionar uma tarefa</button>
    </div>
    <div class="border" v-for="(task, index) in tasks" :key="index">
      <div class="tasks-content">
        <ul>
          <li>{{ task.title }}</li>
          <span @click="removeTask(task)">&times;</span>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: "Tasks",
      currentTask: "",
      tasks: [],
      addedTask: false,
    };
  },
  methods: {
    addTask() {
      if (this.currentTask.length >= 1) {
        this.tasks.push({
          title: this.currentTask,
        });
        (this.currentTask = ""), (this.addedTask = true);
      }
      setTimeout(() => {
        this.addedTask = false;
      }, 2000);
    },

    inputSubmit() {
      this.addTask();
    },
    removeTask(task) {
      this.tasks = this.tasks.filter((t) => t.title != task.title);
    },
  },
};
</script>

<style scoped>
.tasks {
  display: flex;
  flex-direction: column;
  padding: 5rem;
  justify-content: center;
  color: #31f500;
}
.border {
  height: auto;
  width: auto;
  border: 1px solid #333;
  border-radius: 12px;
  margin: .2rem 0;
  padding: 1rem;
}
.tasks h1 {
  color: #fafafa;
}
input {
  width: 250px;
  height: 20px;
  border-radius: 10px;
  padding: 15px;
  background: transparent;
  box-shadow: 0px 0px 18px rgba(0, 0, 0, 0.585);
  color: #31f500;
}
input::-webkit-input-placeholder {
  color: #fafafa;
  font-size: 0.68rem;
}
button {
  margin: 1rem 0;
  background: transparent;
  box-shadow: 0px 0px 18px rgba(0, 0, 0, 0.585);
  border-radius: 10px;
  padding: 10px;
  cursor: pointer;
  color: #fafafa;
  transition: 0.5s ease;
  width: 20%;
  font-weight: bold;
  transform: scale(0.9);
}
button:hover {
  transform: translateY(-5px);
}

ul {
  background: transparent;
  box-shadow: 0px 0px 18px rgba(0, 0, 0, 0.585);
  width: 100%;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  cursor: pointer;
  height: 35px;
  font-weight: bold;
  border-radius: 10px;
  position: relative;
}
span {
  position: absolute;
  right: -2.8rem;
  background: #222;
  box-shadow: 4px 0px 18px black;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 50%;
  height: 40px;
  width: 40px;
  font-size: 1.5rem;
  font-weight: bold;
  color: rgb(172, 172, 172);
  padding: 0 1rem;
}
.tasks-content {
  width: 200px;
}

.success {
  position: fixed;
  left: 2rem;
  top: 1rem;
  width: 250px;
  height: 60px;
  background: #111;
  border-radius: 8px;
  padding: 1rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
  transition: 0.5s ease;
  z-index: 100;
  animation: notification 0.3s linear;
}
.success p {
  height: 40px;
  width: 40px;
  border-radius: 50%;
  border: 2px solid #31f500;
  display: grid;
  place-items: center;
  color: #31f500;
}
@keyframes notification {
  from {
    transform: translateY(-50px);
  }
  to {
    transform: translateY(0px);
  }
}
@media (max-width: 768px) {
  input,
  button {
    width: 100%;
  }
  .tasks {
    align-items: center;
    padding: 2rem;
  }
  .tasks h1 {
    text-align: center;
  }

}
</style>
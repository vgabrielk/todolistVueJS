
<template>
  <div class="tasks">
  <h1>Tasks</h1>
  <input maxlength="12" type="text" @keyup.enter="inputSubmit" v-model="currentTask" />
  <button @click="addTask">Add a new task</button>
    <div class="tasks-content">
      <div v-for="(task, index) in tasks" :key="index">
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
  name: "Tasks",
  data() {
    return {
      tasks: [],
    };
  },
  currentTask: "",
  methods: {
    addTask() {
      if (this.currentTask.length >= 1) {
        this.tasks.push({
          title: this.currentTask,
        });
        this.currentTask = "";
      }
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

}
input {
  width: 30%;
  height: 20px;
  border-radius: 10px;
  padding: 15px;
  background: transparent;
  color: #31f500;
  box-shadow: 0px 0px 18px rgba(0, 0, 0, 0.585);
}
button {
  margin-top: 1rem;
  background: transparent;
  box-shadow: 0px 0px 18px rgba(0, 0, 0, 0.585);
  border-radius: 10px;
  padding: 10px;
  cursor: pointer;
  color: #fafafa;
  transition: 0.5s ease;
  width: 20%;

}
button:hover {
  transform: translateY(-5px);
}
@media(max-width: 768px){
  input, button{
    width: 100%;
  }
  .tasks{
    align-items: center;
  }
}
ul {
  margin-top: 1rem;
  background: transparent;
  box-shadow: 0px 0px 18px rgba(0, 0, 0, 0.585);
  min-width: auto;
  width: auto;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  cursor: pointer;
  height: 35px;

  border-radius: 10px;
  position: relative;
}
span {
  position: absolute;
  right: 0;
  background: red;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 50%;
  height: 40px;
  width: 40px;
  font-size: 1.5rem;
  font-weight: bold;
}
.tasks-content {
  width: 200px;
}
</style>
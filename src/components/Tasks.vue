
<template>
  <div v-if="addedTask" class="success">
    <h5>Task added with success </h5>
    <p> ✔️ </p>
  </div>
  <div class="tasks">
    <div class="row">
    <h1>Tasks</h1>
    <input
    placeholder="Type to add a new task"
      maxlength="22"
      type="text"
      @keypress.enter="inputSubmit"
      v-model="currentTask"
    />
    <button @click="addTask">Add a new task</button>
    </div>
    <div class="tasks-content">
      <div v-for="(task, index) in tasks" :key="index">
        <ul @click="addBackground">
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
      addedTask : false
    };
  },
  methods: {
    addTask() {
      if (this.currentTask.length >= 1) {
        this.tasks.push({
          title: this.currentTask,
        });
        this.currentTask = "",
          this.addedTask = true
      }
          setTimeout(() =>{
      this.addedTask = false
    },1000)
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
  color:#31f500
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
input::-webkit-input-placeholder{
  color: #fafafa;
  font-size: .680rem;
}
button {
  margin-top: 1rem;
  background: transparent;
  box-shadow: 0px 0px 18px rgba(0, 0, 0, 0.585);
  border-radius: 10px;
  padding: 10px;
  cursor: pointer;
  color: #31f500;
  transition: 0.5s ease;
  width: 20%;
  font-weight: bold;
  transform: scale(.9);
}
button:hover {
  transform: translateY(-5px);
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
  font-weight: bold;
  border-radius: 10px;
  position: relative;
}
span {
  position: absolute;
  right: -1rem;
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
}
.tasks-content {
  width: 200px;
}

.isdone {
  background: transparent;
  position: absolute;
  right: -2rem;
}
.success{
  position: fixed;
  right: 1rem;
  top: 1rem;
  width: 250px;
  height: 60px;
  background: #111;
  border-radius: 8px;
  padding: 1rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
  transition: .5s ease;
}
</style>
<script>

import Header from "./components/Header.vue";
import Tasks from "./components/Tasks.vue";

export default {
  el: "#app",
  components: {
    Header,
    Tasks
  },
};
</script>

<template>
  <div id="app">
    <Header />
    <Tasks />
  </div>
</template>

<style>
body {
  background-color: #222;
  color: #fafafa;
}
body::-webkit-scrollbar{
  width: 8px;
  border-radius: 8px;
  background-color: #111; 
}
body::-webkit-scrollbar-button{
  background-color: #31f500 ;
  border-radius:12px;
}
body::-webkit-scrollbar-thumb{
  background-color: #444 ;
  border-radius:12px;
}
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: sans-serif;
  outline: none;
  text-decoration: none;
  border: none;
  -webkit-user-select: #31f500;
  user-select: #31f500;
  list-style: none;
}
.container{
  width: 90%;
  display: flex;
  justify-content: center;
}
</style>

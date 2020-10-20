<template>
<div id="app">
  <h1>Got some shit to do, Lazy.</h1>
  <ul>
    <li v-for="(todo, index) in tasks"
    v-bind:key="index" :class="todo.priority">
      <span>{{ todo.task }}</span>
      <!-- <span v-if="todo.highPriority">DO IT NOW!</span> -->
    </li>
  </ul>

<form v-on:submit.prevent="saveNewTask">
    <label for="new-task">More shit to do:</label>
    <input type="text" id="new-task" v-model="newTask.task">
        <input type="radio" name= "priority" id="high-priority" value="high-priority" for ="high" v-model="newTask.priority">High</input>
        <input type="radio" name = "priority" id="low-priority" value="low-priority" for="low" v-model="newTask.priority" checked>Low</input>
    <button type="submit" value="save-new-task">Add it</button>
</form>
</div>
  
</template>

<script>
export default {
    data() {
        return {
            tasks: [],
          newTask: {
            task:"",
            priority:""
          }
        }
    },

  methods:  {
    saveNewTask: function () {
      this.tasks.push({
        task: this.newTask.task, 
        priority: this.newTask.priority
      }),
    this.newTask = {
      task: "",
      priority: ""
    };
    },
  
    handleClick: function(index) {
        this.tasks[index].highPriority = true;
    }
  }  
}

</script>



<style>
#app {
  width: 60%;
  margin: 0 auto;
  font-family: 'Lato', sans-serif;
}

ul {
  margin: 0;
  padding: 0;
  list-style-type: none;
}

li {
  margin: 20px 0;
  padding: 10px;
  display: flex;
  justify-content: space-between;
}

li span {
  padding: 8px;
}

li button {
  background: #f2360c;
  color: #fff;
  border: none;
  padding: 10px;
  cursor: pointer;
}

li.low-priority {
  border: 2px solid #1a681e;
  color: #1a681e;
}

li.high-priority {
  border: 2px solid #f2360c;
}

input[type="text"] {
  padding: 10px;
  width: 50%;
  margin:5px;
}

button, input[type="submit"]{
  padding: 10px;
  background: #000;
  color: #fff;
  cursor: pointer;
  border: 1px solid #000;
}

</style>
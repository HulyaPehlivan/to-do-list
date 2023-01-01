<template>
  <div class="todo-list">
    <h1>To-do List</h1>
        <!-- The form for adding new tasks -->
    <form @submit.prevent="addTask" class="add-task-form">
      <input v-model="newTask" placeholder="Add a new task" required/>
      <button type="submit">Add</button>
    </form>
    <ul>
            <!-- A list item for each task in the tasks list -->
      <li v-for="(task, index) in tasks" :key="index" :class="{ 'completed': task.completed }">
        {{ task.title }}
                <!-- The "Complete" button for marking the task as completed -->
        <button @click="completeTask(index)">Complete</button>
                <!-- The "Remove" button for removing the task from the list -->
        <button @click="removeTask(index)">Remove</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTask: '',
      tasks: [
        {
          title: 'Sample to-do item',
          completed: false
        }
      ]
    }
  },
  methods: {
    addTask() {
        this.tasks.push({
        title: this.newTask,
        completed: false
      })
      this.newTask = ''
    },
    completeTask(index) {
      this.tasks[index].completed = true
    },
    removeTask(index) {
      this.tasks.splice(index, 1)
    }
  }
}
</script>

<style>
.todo-list {
  max-width: 500px;
  margin: 0 auto;
  text-align: center;
}

h1 {
  font-size: 2em;
  margin-bottom: 20px;
  font-family: Cambria, Cochin, Georgia, Times, 'Times New Roman', serif;
}

.add-task-form {
  display: flex;
  justify-content: center;
  align-items: center;
}

.add-task-form input {
  width: 75%;
  padding: 10px;
  font-size: 1em;
  border: none;
  border-radius: 50px;
}

.add-task-form button {
  width: 100px;
  padding: 10px;
  font-size: 1em;
  border: none;
  border-radius: 50px; /*Round corners*/
  background-color: #4caf50;
  color: white;
  cursor: pointer;
  margin-bottom: 5px; /* To leave some space between the to-do list items*/
}

ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 10px;
  padding: 10px;
  border-radius: 50px;
  background-color: #f1f1f1;
}

li button {
  width: 100px;
  padding: 10px;
  font-size: 0.8em;
  border: none;
  border-radius: 50px; /*Round corners*/
  cursor: pointer;
}

li button:nth-of-type(1) {
  background-color: #4caf50;
  color: white;
  margin-left: auto;
}

li button:nth-of-type(2) {
  background-color: #f44336;
  color: white;
  margin-left: 10px;
}

.completed {
  text-decoration: line-through;
  color: #ccc;
}
</style>

<script>
   import TaskBoard from './lib/TaskBoard.svelte';
  import Header from './lib/Header.svelte';
  import { onMount } from 'svelte';

  let tasks = []; // Array to store tasks

  // Function to fetch tasks from the API
  const fetchTasks = async () => {
    try {
      const response = await fetch('http://localhost:3500/tasks');
      if (response.ok) {
        tasks = await response.json();
      }
    } catch (error) {
      console.error("Error fetching tasks:", error);
    }
  };

  // Function to add a new task
  const addTask = (newTask) => {
    tasks = [...tasks, newTask]; // Add the new task to the task list
  };

  onMount(fetchTasks); // Fetch tasks when the component mounts
</script>

<Header onAddTask={addTask} />
<main>
  <TaskBoard tasks={tasks} />
</main>

<style>
  main {
    height: 100%;
    width: 100%;
  }
</style>

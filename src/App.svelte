<script lang="ts">
  import { onMount } from "svelte";

  import NewTask from "./components/NewTask.svelte";
  import Task from "./components/Task.svelte";
  import TaskActions from "./components/TaskActions.svelte";

  let allTasks = [];
  let newTaskInput = false;

  function newTaskHandler(e) {
    const newTask = e.detail;
    console.log("new Task is ", JSON.stringify(newTask));
    allTasks = [...allTasks, newTask];
    newTaskInput = false;
  }

  $: {
    //   saving tasks to localstorage
    if (allTasks?.length > 0) {
      localStorage.setItem("allTasks", JSON.stringify(allTasks));
    }
  }

  function getSavedTask(): any[] {
    try {
      let storedTask: any[] = JSON.parse(localStorage.getItem("allTasks"));
      return storedTask;
    } catch (error) {
      console.log(error);
      return null;
    }
  }
  onMount(() => {
    const savedTasks = getSavedTask();
    if (savedTasks) {
      allTasks = savedTasks;
    }
  });
</script>

<main>
  <h1>Svelte Task APP !!</h1>
  <div class="todo">
    <TaskActions on:addTask={() => (newTaskInput = true)} />
    {#each allTasks as task}
      <Task {...task} />
    {:else}
      <Task />
    {/each}
    {#if newTaskInput}
      <NewTask bind:newTaskInput on:newTask={newTaskHandler} />
    {/if}
  </div>
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 70rem;
    margin: 0 auto;
  }

  h1 {
    color: #00c3ff;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  .todo {
    width: 60%;
    margin: 0 auto;
  }
  @media (max-width: 632px) {
    .todo {
      width: 100%;
      margin: 0 auto;
    }
  }
</style>

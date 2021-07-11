<script lang="ts">
  import NewTask from "./components/NewTask.svelte";
  import Task from "./components/Task.svelte";
  import TaskActions from "./components/TaskActions.svelte";
</script>

<main>
  <h1>Svelte TODO APP !!</h1>
  <div class="todo">
    <TaskActions />
    <Task />
    <NewTask />
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
</style>

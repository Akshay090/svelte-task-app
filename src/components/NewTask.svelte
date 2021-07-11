<script>
  import Close24 from "carbon-icons-svelte/lib/Close24";
  import Checkmark24 from "carbon-icons-svelte/lib/Checkmark24";
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  export let newTaskInput;
  let name = "";

  function closeClick() {
    newTaskInput = false;
  }

  function addTask() {
    const newTask = {
      name,
      isActive: false,
      time: 0,
    };
    dispatch("newTask", newTask);
  }
</script>

<div class="task">
  <div class="task-body">
    <input
      bind:value={name}
      class="task-input"
      type="text"
      placeholder="Write your New Task"
    />
  </div>

  <div class="task-actions">
    <div class="icon-bg">
      <Close24 class="icon" on:click={closeClick} />
    </div>
    <div class="icon-bg">
      <Checkmark24 class="icon" on:click={addTask} />
    </div>
  </div>
</div>

<style>
  .task {
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-radius: 8px;
    box-shadow: #b7b7b71a 0px 4px 13px 4px;
    padding: 4px 8px;
    color: #31bbf3;
    padding: 8px;
  }
  .task-body {
    display: flex;
    justify-content: center;
    align-items: center;
    margin-left: 8px;
    width: 100%;
  }

  .task-input {
    width: 100%;
    padding: 8px;
    margin: 0;
    background-color: darkgray;
    border: none;
    outline: none;
    border-radius: 8px;
  }
  .task-actions {
    display: flex;
  }

  :global(svg.icon) {
    fill: #31bbf3;
  }
  .icon-bg {
    background-color: #31bcf328;
    margin-left: 8px;
  }
</style>

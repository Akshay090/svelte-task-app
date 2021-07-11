<script>
  import AddAlt24 from "carbon-icons-svelte/lib/AddAlt24";
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();
  function addTaskEvent() {
    dispatch("addTask", null);
  }
</script>

<div class="task-actions">
  <div class="day">Today</div>

  <div class="actions">
    <div class="add" on:click={addTaskEvent}>
      <AddAlt24 /> <span>Add Taks</span>
    </div>
  </div>
</div>

<style>
  .task-actions {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 4px 8px;
    color: #31bbf3;
    margin-bottom: 18px;
  }
  .day {
    font-weight: 800;
    color: lightblue;
    font-size: larger;
  }
  .add {
    display: flex;
    align-items: center;
    border-radius: 8px;
    box-shadow: #b7b7b71a 0px 4px 13px 4px;
    background-color: #3742464a;
    padding: 4px;
    cursor: pointer;
  }
  .add span {
    margin-left: 8px;
    margin-right: 8px;
  }
</style>

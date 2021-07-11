<script>
  import PlayOutlineFilled24 from "carbon-icons-svelte/lib/PlayOutlineFilled20";
  import PauseOutlineFilled24 from "carbon-icons-svelte/lib/PauseOutlineFilled24";

  export let name = "Create a New Task 🎉";
  export let isActive = false;
  export let time = 0;

  let interval = null;

  function secondsToHms(d) {
    d = Number(d);

    var h = Math.floor(d / 3600);
    var m = Math.floor((d % 3600) / 60);
    var s = Math.floor((d % 3600) % 60);
    return (
      ("0" + h).slice(-2) +
      ":" +
      ("0" + m).slice(-2) +
      ":" +
      ("0" + s).slice(-2)
    );
  }

  $: {
    if (isActive && !interval) {
      interval = setInterval(() => {
        time += 1;
      }, 1000);
    }
    if (!isActive && interval) {
      clearInterval(interval);
      interval = null;
    }
  }
</script>

<div class="task">
  <div class="task-body">
    <button class="complete-btn" />
    <p class="title">{name}</p>
  </div>

  <div class="task-actions disable-select">
    {#if isActive}
      <div class="status">
        <div class="dot" />
        <div class="text">In progress</div>
      </div>
    {/if}

    {#if isActive}
      <PauseOutlineFilled24
        class="action-icon"
        on:click={() => (isActive = false)}
      />
    {:else}
      <PlayOutlineFilled24
        class="action-icon"
        on:click={() => (isActive = true)}
      />
    {/if}
    <div class="time"><p>{secondsToHms(time)}</p></div>
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
    margin-bottom: 12px;
  }
  .complete-btn {
    width: 20px;
    height: 20px;
    border-radius: 50%;
    margin: auto;
    background-color: #cbe2ea;
  }
  .complete-btn:hover {
    filter: brightness(95%);
  }
  .title {
    font-weight: 800;
    margin-left: 8px;
    word-break: break-word;
  }
  .task-body {
    display: flex;
    justify-content: center;
    align-items: center;
    margin-left: 8px;
  }
  :global(svg.action-icon) {
    fill: #31bbf3;
    width: 50px;
    height: 25px;
    cursor: pointer;
  }

  .task-actions {
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .task-actions p {
    background-color: #4a4c50;
    padding: 4px 6px;
    border-radius: 8px;
  }

  .status {
    display: flex;
    align-items: center;
  }
  .status .dot {
    height: 5px;
    width: 5px;
    background: rgb(91, 227, 151);
    margin-right: 0.25rem;
    border-radius: 999px;
  }
  .status .text {
    color: rgb(91, 227, 151);
    font-size: 0.75rem;
    font-weight: 500;
  }

  .disable-select {
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
  }
</style>

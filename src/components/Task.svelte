<script>
  import PlayOutlineFilled24 from "carbon-icons-svelte/lib/PlayOutlineFilled20";

  let name = "My Task 1";
</script>

<div class="task">
  <div class="task-body">
    <button class="complete-btn" />
    <p class="title">{name}</p>
  </div>

  <div class="task-actions">
    <PlayOutlineFilled24 class="play" />
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
  }
  .task-body {
    display: flex;
    justify-content: center;
    align-items: center;
    margin-left: 8px;
  }
  :global(svg.play) {
    fill: #31bbf3;
    width: 50px;
    height: 25px;
  }
</style>

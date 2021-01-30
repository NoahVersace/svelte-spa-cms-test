<script>
  import { usePreloading } from "svelte-navigator";
  const preloading = usePreloading();
  let inProgress = false;
  let width = 0;

  $: {
    if ($preloading && !inProgress) {
      inProgress = true;
      width = 40;
      console.log("ja");
    } else if (!$preloading && inProgress) {
      width = 100;
      console.log("test");
      setTimeout(() => {
        inProgress = false;
        width = 0;
      }, 500);
    }
  }
</script>

<div class="loading-indicator" class:hide={!inProgress}>
  <div class="loading-bar" style="width: {width}%" />
</div>

<style>
  .loading-indicator {
    position: fixed;
    top: 0;
    width: 100vw;
    height: 3px;

    pointer-events: none;
  }

  .loading-bar {
    height: 100%;
    background: rgb(54, 54, 54);
    transition: width 400ms ease-out;
  }

  .hide {
    opacity: 0;
  }
</style>

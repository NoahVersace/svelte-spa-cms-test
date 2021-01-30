<script>
  import { usePreloading } from "svelte-navigator";
  import { tweened } from "svelte/motion";

  const preloading = usePreloading();
  let inProgress = false;
  let translateX = tweened(100);
  let fadeOut = false;
  let preparationFinished = false;

  $: {
    if ($preloading && !inProgress) {
      inProgress = true;
      requestAnimationFrame(() => {
        translateX.set(85);
        setTimeout(() => (preparationFinished = true), 800);
      });
    } else if (!$preloading && inProgress && preparationFinished) {
      translateX.set(0);
      setTimeout(() => {
        fadeOut = true;
      }, 800);
      setTimeout(() => {
        inProgress = false;
        fadeOut = false;
        preparationFinished = false;
        translateX.set(100);
      }, 1000);
    }
  }
</script>

<!-- <progress value={$translateX} /> -->

<div class="loading-indicator" class:hide={!inProgress}>
  <div
    class="loading-bar"
    style="transform: translateX(-{$translateX}%) translateZ(0); opacity: {fadeOut
      ? 0
      : 1}"
  />
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
    height: 2px;
    background: rgb(54, 54, 54);
    transition: transform 800ms, opacity 200ms;
    backface-visibility: hidden;
    perspective: 1000;
    -webkit-transform: translateZ(0);
    -moz-transform: translateZ(0);
    -ms-transform: translateZ(0);
    -o-transform: translateZ(0);
    will-change: transform;
  }

  .hide {
    opacity: 0;
  }
</style>

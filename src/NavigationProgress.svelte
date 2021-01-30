<script>
  import { usePreloading } from "svelte-navigator";
  import { tweened } from "svelte/motion";
  import { cubicInOut } from "svelte/easing";

  const preloading = usePreloading();

  $: if ($preloading) animate();

  let ready = true;
  let hide = true;
  let value = tweened(0, { duration: 400, easing: cubicInOut });

  async function animate() {
    if (ready) {
      hide = false;
      await value.set(0.2);
      await value.set(1);
      hide = true;
      await new Promise((res) => setTimeout(res, 200));
      value.set(0, { duration: 0 });
    }
  }
</script>

<progress value={$value} class:hide />

<!-- <div class="bg-red-500 h-52 animate-bounce">fds</div> -->
<style>
  progress {
    position: fixed;
    top: 0;
    left: 0;
    height: 4px;
    width: 100%;
    transition: opacity 200ms;
    background: transparent;
  }

  progress::-webkit-progress-value {
    background: rgb(93, 109, 250);
  }

  progress::-webkit-progress-bar {
    background: rgb(92, 92, 92);
  }

  .hide {
    opacity: 0;
  }
</style>

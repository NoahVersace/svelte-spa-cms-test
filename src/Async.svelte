<script context="module">
  import { notion, Notion } from "@noahsalvi/svelte-notion";
  let blocks;

  export async function preload() {
    blocks = await notion.fetchPage("4f20c8765bf84abbb96ae4aa7de04c32", window);
  }
</script>

<script>
  export let location;
  export let navigate;
</script>

{#if blocks}
  <h1>Preloading in SPA</h1>
  <Notion {blocks} />
{:else}
  Lorem ipsum dolor sit amet consectetur adipisicing elit. Inventore natus
  perspiciatis at minus quis optio, corporis non unde iste ex ad ullam,
  blanditiis soluta reprehenderit, sunt nihil saepe a! Atque.
  <div class="bg-red h-full" />
{/if}

<script>
  import { notion, Notion } from "@noahsalvi/svelte-notion";
  const loadNotion = () =>
    notion.fetchPage("4f20c8765bf84abbb96ae4aa7de04c32", window);
</script>

{#await loadNotion()}
  <div class="loading">Loading</div>
{:then blocks}
  <Notion {blocks} />
{/await}

<style>
  .loading {
    min-height: 100vh;
    /* background: red; */
  }
</style>

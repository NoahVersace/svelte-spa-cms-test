<script>
  import { notion, Notion } from "@noahsalvi/svelte-notion";
  const loadNotion = () =>
    notion.fetchPage("8f2e3a91cb374fde8d7b608e82681f32", window);
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

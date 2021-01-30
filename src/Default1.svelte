<script>
  import { notion, Notion } from "@noahsalvi/svelte-notion";
  const loadNotion = () =>
    notion.fetchPage("81e2900071d64d9893f844525af2ccdd", window);
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

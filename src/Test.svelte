<script>
  import { notion, Notion } from "@noahsalvi/svelte-notion";
  const loadNotion = () =>
    notion.fetchPage("81e2900071d64d9893f844525af2ccdd", window);
</script>

{#await loadNotion()}
  loading
{:then blocks}
  <Notion {blocks} />
{/await}
test

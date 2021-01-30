<script context="module">
  import { notion, Notion } from "@noahsalvi/svelte-notion";
  let blocks;

  export async function preload() {
    blocks = await notion.fetchPage("4f20c8765bf84abbb96ae4aa7de04c32", window);
  }
</script>

<Notion {blocks} />

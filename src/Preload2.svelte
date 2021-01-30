<script context="module">
  import { notion, Notion } from "@noahsalvi/svelte-notion";
  let blocks;

  export async function preload() {
    blocks = await notion.fetchPage("41bc0af7b5f241108688619e2016bded", window);
  }
</script>

<Notion {blocks} />

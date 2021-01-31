<script lang="ts">
  import Tailwindcss from "./Tailwindcss.svelte";
  import { Router, Route, Link } from "svelte-navigator";
  import Default1 from "./Default1.svelte";
  import Default2 from "./Default2.svelte";
  import * as Preload2 from "./Preload2.svelte";
  import NavigationProgress from "./NavigationProgress.svelte";
</script>

<Tailwindcss />
<Router>
  <!-- <LoadingIndicator /> -->
  <NavigationProgress />

  <div class="p-5">
    <h1 class="text-3xl">Preloading:</h1>
    <div class="m-2" />
    <Link
      to="preload1"
      class="bg-indigo-300 p-3 rounded hover:bg-indigo-400 inline-block"
    >
      Preload 1
    </Link>
    <Link
      to="preload2"
      class="bg-indigo-300 p-3 rounded hover:bg-indigo-400 inline-block"
    >
      Preload 2
    </Link>
    <div class="m-4" />

    <h1 class="text-3xl">Default:</h1>
    <div class="m-2" />
    <Link
      to="default1"
      class="bg-indigo-300 p-3 rounded hover:bg-indigo-400 inline-block"
    >
      Default 1
    </Link>
    <Link
      to="default2"
      class="bg-indigo-300 p-3 rounded hover:bg-indigo-400 inline-block"
    >
      Default 2
    </Link>
    <div class="m-4" />
    <div class="w-100" />
    <Route path="">Home</Route>
    <Route path="default1" component={Default1} />
    <Route path="default2" component={Default2} />
    <Route path="preload1" preload={() => import("./Preload1.svelte")} />
    <Route path="preload2" preload={() => Preload2} />
  </div>
</Router>

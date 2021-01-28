<script lang="ts">
  import Tailwind from "./Tailwind.svelte";
  import { Link, Route, Router } from "svelte-routing";
  import Test from "./Test.svelte";
  import Test2 from "./Test2.svelte";
  export let url = "";
</script>

<Tailwind />

<Router {url}>
  <div>
    <Route path="home">
      <Link to="/t1">T1</Link>
      <Link to="/t2">T2</Link>
    </Route>
    <Route path="t1" component={Test} />
    <Route path="t2" component={Test2} />
  </div>
</Router>

<script lang="ts">
  import Tailwind from "./Tailwind.svelte";
  import { Link, Route, Router } from "svelte-navigator";
  import Test from "./Test.svelte";
  import Test2 from "./Test2.svelte";
</script>

<Tailwind />

<Router>
  <div>
    <Route path="">
      <Link to="/t1">T1</Link>
      <Link to="/t2">T2</Link>
    </Route>
    <Route path="t1" component={Test} />
    <Route path="t2" component={Test2} />
  </div>
</Router>

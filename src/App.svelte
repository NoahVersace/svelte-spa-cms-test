<script lang="ts">
  import ModeSwitcher from "./ModeSwitcher.svelte";
  import Tailwindcss from "./Tailwindcss.svelte";
  import { Router, Route, Link } from "svelte-navigator";
  import Test1 from "./Test1.svelte";
  import Test2 from "./Test2.svelte";
</script>

<Tailwindcss />
<ModeSwitcher />
<Router>
  <Link to=""><button>Home</button></Link>
  <Link to="test-1"><button>Test1</button></Link>
  <Link to="test-2"><button>Test2</button></Link>
  <div class="w-100" />
  <Route path="">Home</Route>
  <Route path="test-1" component={Test1} />
  <Route path="test-2" component={Test2} />
</Router>

<style>
  button {
    background: white;
    color: black;
    padding: 10px 30px;
    margin: 5px 50px;
  }
</style>

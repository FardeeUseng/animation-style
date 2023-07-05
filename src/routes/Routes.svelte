<script>
  import { Router, Route } from "svelte-routing";
  import Views from "../views/index.svelte";
</script>

<Router>
  <Route path="/" component={Views} />
</Router>

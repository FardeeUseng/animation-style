<script>
  import { Router, Route } from "svelte-routing";
  import HomePage from "../views/home-page/index.svelte";
  import AnimBasic from "../views/anim-basic/index.svelte";
</script>

<Router>
  <Route path="/" component={HomePage} />
  <Route path="/basic" component={AnimBasic} />
</Router>

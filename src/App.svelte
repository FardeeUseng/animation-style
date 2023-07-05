<script>
  import Navbar from "./components/navbar/Navbar.svelte";
  import View from "./views/index.svelte";
</script>

<Navbar />
<View />

<style>
  :global(*, body) {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
</style>

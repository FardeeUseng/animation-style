<script>
  import Navbar from "./components/navbar/Navbar.svelte";
  import Routes from "./routes/Routes.svelte";
  // import View from "./views/index.svelte";
</script>

<Navbar />
<Routes />

<style>
  :global(*, body) {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
  :global(body) {
    background-color: #dfdfdf;
  }
</style>

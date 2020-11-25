<script>
  import Nav from "../components/Nav.svelte";
  import Footer from "../components/Footer.svelte";

  export let segment;
</script>

<style>
  :global(body) {
    display: flex;
    flex-direction: column;
    /* align-items: center; */
    width: 100%;
    min-height: 100vh;
  }
  main {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    position: relative;
    max-width: 960px;
    background-color: white;
    padding: 3em;
    margin: 0 auto;
    box-sizing: border-box;
  }
</style>

<Nav {segment} />

<main>
  <slot />
</main>

<Footer />

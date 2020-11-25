<script>
  import { fade, fly } from "svelte/transition";
  import FancyCard from "../components/FancyCard.svelte";
</script>

<style>
  /* main {
    display: grid;
    grid-template-columns: 1fr 1fr;
  } */

  main {
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;
  }

  @media only screen and (max-width: 865px) {
    main {
      display: block;
      margin: auto;
    }
  }
</style>

<svelte:head>
  <title>Sapper project template</title>
</svelte:head>

<main in:fade={{ delay: 400 }} out:fly={{ x: 1000 }}>
  <FancyCard />
  <FancyCard blur />
  <FancyCard fx />
  <FancyCard raise />
  <FancyCard
    raise
    title="Custom Title"
    content="Lorem ipsum dolor sit amet consectetur adipisicing elit. Hic sequi
    corrupti dolore aspernatur, earum enim reiciendis repellendus quae quos
    mollitia labore aliquid nostrum ratione iste cumque. Officiis quo accusamus
    atque aliquid quaerat!" />
</main>

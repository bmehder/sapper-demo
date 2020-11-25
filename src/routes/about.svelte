<script>
  import { fade, fly } from "svelte/transition";
</script>

<svelte:head>
  <title>About</title>
</svelte:head>

<main in:fade={{ delay: 400 }} out:fly={{ x: 1000 }}>
  <h1>About this site</h1>

  <p>This is the 'about' page. There's not much here.</p>
</main>

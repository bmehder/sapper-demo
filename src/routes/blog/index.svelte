<script context="module">
  export function preload() {
    return this.fetch(`blog.json`)
      .then(r => r.json())
      .then(posts => {
        return { posts };
      });
  }
</script>

<script>
  import { fade, fly } from "svelte/transition";
  import FancyCard from "../../components/FancyCard.svelte";
  export let posts;
</script>

<style>
  ul {
    margin: 0 6em;
  }
  li {
    margin: 0.5em 0;
  }
</style>

<svelte:head>
  <title>Blog</title>
</svelte:head>

<main in:fade={{ delay: 400 }} out:fly={{ x: 1000 }}>
  <section>
    <FancyCard title="Recent posts" content="">
      <ul>
        {#each posts as post}
          <!-- we're using the non-standard `rel=prefetch` attribute to
				tell Sapper to load the data for the page as soon as
				the user hovers over the link or taps it, instead of
				waiting for the 'click' event -->
          <li>
            <a rel="prefetch" href="blog/{post.slug}">{post.title}</a>
          </li>
        {/each}
      </ul>
    </FancyCard>
  </section>
</main>

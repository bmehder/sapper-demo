<script context="module">
  export async function preload({ params }) {
    // the `slug` parameter is available because
    // this file is called [slug].svelte
    const res = await this.fetch(`blog/${params.slug}.json`);
    const data = await res.json();

    if (res.status === 200) {
      return { post: data };
    } else {
      this.error(res.status, data.message);
    }
  }
</script>

<script>
  import { fade, fly } from "svelte/transition";
  export let post;
</script>

<style>
  /*
		By default, CSS is locally scoped to the component,
		and any unused styles are dead-code-eliminated.
		In this page, Svelte can't know which elements are
		going to appear inside the {{{post.html}}} block,
		so we have to use the :global(...) modifier to target
		all elements inside .content
	*/
  .content :global(h2) {
    font-size: 1.4em;
    font-weight: 500;
  }

  .content :global(pre) {
    background-color: #f9f9f9;
    box-shadow: inset 1px 1px 5px rgba(0, 0, 0, 0.05);
    padding: 0.5em;
    border-radius: 2px;
    overflow-x: auto;
  }

  .content :global(pre) :global(code) {
    background-color: transparent;
    padding: 0;
  }

  .content :global(ul) {
    line-height: 1.5;
  }

  .content :global(li) {
    margin: 0 0 0.5em 0;
  }
  a {
    display: inline-block;
    margin: 1em 0 2em;
    padding: 0.5em 1em;
    background-color: rgb(255, 62, 0);
    color: white;
    border-radius: 4px;
    font-size: 0.8em;
    text-decoration: none;
  }
</style>

<svelte:head>
  <title>{post.title}</title>
</svelte:head>

<main in:fade={{ delay: 400 }} out:fly={{ x: 1000 }}>
  <a href="/blog">&laquo; Back</a>
  <h1>{post.title}</h1>

  <div class="content">
    {@html post.html}
  </div>
</main>

<script>
  export let title = "Title";
  export let content = "Enter your content as text or html.";
  export let raise = false;
  export let blur = false;
  export let fx = false;
</script>

<style>
  main {
    margin: 2rem 0;
    /* min-width: 400px; */
    padding: 2rem;
    /* 		min-width: 400px; */
    background: white;
    background-image: linear-gradient(
      to bottom,
      transparent,
      rgba(0, 0, 0, 0.05)
    );
    border-radius: 4px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.24);
  }
  span {
    display: inline-block;
    padding: 1rem;
    border-radius: 4px;
  }
  h1 {
    display: flex;
    align-items: center;
    justify-content: center;
    margin: 0;
    color: #555;
    font-size: 2rem;
  }
  h1::before,
  h1::after {
    content: "";
    display: flex;
    flex: 1;
    height: 2rem;
  }

  :global(h1.fx::before, h1.fx::after) {
    animation: fx 3s infinite alternate-reverse ease-in-out;
  }

  :global(h1.blur::before, h1.blur::after) {
    filter: blur(10px);
  }

  .raise {
    box-shadow: 0px 30px 20px rgba(0, 0, 0, 0.25);
  }

  @keyframes fx {
    from {
      filter: blur(0px);
    }
    to {
      filter: blur(20px);
    }
  }

  h1::before {
    background: linear-gradient(to left, #40e0d0, #ff8c00, #ff0066);
    border-top-left-radius: 4px;
    border-bottom-left-radius: 4px;
  }
  h1::after {
    background: linear-gradient(to right, #40e0d0, #ff8c00, #ff0066);
    border-top-right-radius: 4px;
    border-bottom-right-radius: 4px;
  }
  h1 span {
    text-align: center;
  }
  p {
    color: #555;
    line-height: 1.4em;
    margin: 0;
    display: flex;
    justify-content: center;
  }
</style>

<main class:raise>
  <h1 class:blur class:fx contenteditable>
    <span>{title}</span>
  </h1>
  <p>
    <span>
      {@html content}
      <slot />
    </span>
  </p>
</main>

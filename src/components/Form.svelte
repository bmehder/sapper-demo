<script>
  import { onMount } from "svelte";
  export let formID = "";

  let name, email, message, isEmpty;
  let submitted = false;

  onMount(() => {
    const form = document.querySelector("form");
    form.addEventListener("submit", e => {
      e.preventDefault();
      if (
        name.value.length !== 0 &&
        email.value.length !== 0 &&
        message.value.length !== 0
      ) {
        const data = new URLSearchParams(new FormData(form));
        fetch(formID, {
          method: "POST",
          body: data
        });
        submitted = true;
        form.reset();
      } else {
        isEmpty = true;
      }
    });
  });
</script>

<style>
  form {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    margin: auto;
  }
  input,
  textarea,
  button {
    display: block;
    width: 100%;
    margin: 1em;
    padding: 1em;
    border: none;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.24);
    outline: none;
  }
  button {
    background-color: rgb(255, 62, 0);
    color: white;
    padding: 1em 2em;
    font-size: 1em;
    font-weight: bold;
    outline: none;
  }
  button:hover {
    background-image: linear-gradient(
      to bottom,
      rgba(0, 0, 0, 0.05),
      rgba(0, 0, 0, 0.05)
    );
  }
  p {
    color: red;
  }
  h3 {
    color: green;
    text-align: center;
  }
  @media (max-width: 400px) {
  }
</style>

<form action={formID} method="POST">
  <input
    bind:this={name}
    on:focus={() => {
      isEmpty = false;
    }}
    type="text"
    name="name"
    placeholder="Enter name..."
    validate />
  <input
    bind:this={email}
    on:focus={() => {
      isEmpty = false;
    }}
    type="email"
    name="email"
    placeholder="Enter email..."
    validate />
  <textarea
    bind:this={message}
    on:focus={() => {
      isEmpty = false;
    }}
    rows="3"
    name="message"
    placeholder="Enter message..."
    validate />
  <button type="submit" disabled={isEmpty}>Send Message</button>
  {#if isEmpty}
    <p>Please fill out all fields...or else.</p>
  {/if}
</form>

{#if submitted}
  <h3>The form was successfully submitted.</h3>
{/if}

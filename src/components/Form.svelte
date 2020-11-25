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
    max-width: 400px;
    margin: auto;
  }
  input,
  textarea,
  button {
    display: block;
    width: 100%;
    margin: 1em;
    padding: 0.5em 1em;
  }
  button {
    padding: 1em 2em;
    font-weight: bold;
  }
  p {
    color: red;
  }
  h3 {
    color: green;
    text-align: center;
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

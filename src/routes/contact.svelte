<script>
  import { fade, fly } from "svelte/transition";
  import Form from "../components/Form.svelte";
</script>

<style>
  h1 {
    text-align: center;
  }
</style>

<main in:fade={{ delay: 400 }} out:fly={{ x: 1000 }}>
  <h1>Contact Us</h1>

  <Form formID="https://getform.io/f/a00cc437-28ef-4af0-9827-9ce088c22bf5" />
</main>

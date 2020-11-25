<script>
  import { fade, fly } from "svelte/transition";
  import FancyCard from "../components/FancyCard.svelte";
  import Form from "../components/Form.svelte";
</script>

<style>

</style>

<main in:fade={{ delay: 400 }} out:fly={{ x: 1000 }}>
  <FancyCard title="Contact Us" content="">
    <Form formID="https://getform.io/f/a00cc437-28ef-4af0-9827-9ce088c22bf5" />
  </FancyCard>
</main>

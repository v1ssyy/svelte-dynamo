<script>
  import { onMount } from "svelte";

  let message = "";
  let count = 0;

  onMount(async () => {
    try {
      const res = await fetch("http://localhost:5000/api/getCount");
      const json = await res.json();
      message = json;
    } catch (error) {
      console.error(error);
    }
  });

  function handleClick() {
    count += 1;
  }
</script>

<main>
  <h1>message: {message}</h1>
  <button on:click={handleClick}>
    clicks: {count}
  </button>
</main>

<style>
</style>

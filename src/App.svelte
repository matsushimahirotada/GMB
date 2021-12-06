<script lang="ts">
  import Tailwindcss from "./Tailwindcss.svelte";
  import Vote from "./components/vote.svelte";
  import Header from "./components/Header.svelte";

  export let name: string;
</script>

<Header />
<main class="pt-96">
  <Vote />
</main>

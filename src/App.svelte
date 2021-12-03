<script lang="ts">
  import Tailwindcss from "./Tailwindcss.svelte";
  import Header from "./components/Header.svelte";

  export let name: string;

  function click1() {
    alert("1に投票されました");
  }

  function click2() {
    alert("2に投票されました");
  }
</script>

<Header />
<main class="pt-96">
  <p><button class=" btn btn-blue" on:click={click1}>1に投票</button></p>
  <p><button class="btn btn-blue" on:click={click2}>2に投票</button></p>
</main>

<style>
  .btn {
    @apply font-bold py-2 px-4 rounded;
  }
  .btn-blue {
    @apply bg-blue-500 text-white;
  }
  .btn-blue:hover {
    @apply bg-blue-700;
  }
</style>

<script lang="ts">
  import { writable } from "svelte/store";
  import { tweened } from "svelte/motion";
  import { cubicOut } from "svelte/easing";
  import { onMount } from "svelte";

  const tweenedA = tweened(0, {
    duration: 400,
    easing: cubicOut,
  });
  const tweenedB = tweened(0, {
    duration: 400,
    easing: cubicOut,
  });

  let count1: number = 0;
  let count2: number = 0;

  $: allcount = count1 + count2;
  $: persentA = Math.floor((100 / allcount) * count1);
  $: persentB = Math.floor((100 / allcount) * count2);
  $: tweenedA.set(persentA);
  $: tweenedB.set(persentB);
  $: console.log(tweenedA);

  function click1() {
    count1 += 1;
  }

  function click2() {
    count2 += 1;
  }
</script>

<div class="p-10">
  <div class="box-border h-12 w-60 border-4 border-gray-200 bg-gray-500">
    <div class="percent percent-a" style="width: {$tweenedA}%" />
  </div>
  <div class="box-border h-12 w-60 border-4 border-gray-200 bg-gray-500">
    <div class="percent percent-b" style="width: {$tweenedB}%" />
  </div>
  <p><button class=" pt-10 btn btn-blue" on:click={click1}>1に投票</button></p>
  <p class="pt-10">
    <button class=" btn btn-blue" on:click={click2}>2に投票</button>
  </p>
</div>

<style>
  :root {
    --base-width: 100%;
  }
  .answer {
    background: #fafafa;
    cursor: pointer;
    margin: 10px auto;
    position: relative;
  }
  .answer:hover {
    opacity: 0.6;
  }
  .percent {
    height: 100%;
    position: relative;
    box-sizing: border-box;
  }
  .percent-a {
    width: --base-width;
    background: rgba(217, 27, 66, 0.2);
    border-left: 4px solid #d91b42;
  }
  .percent-b {
    background: rgba(69, 196, 150, 0.2);
    border-left: 4px solid #45c496;
  }
  progress {
    display: block;
    width: 100%;
  }
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

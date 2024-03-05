<script>
  import { onMount } from 'svelte'
  import { fade } from 'svelte/transition'

  let str = []

  let rcolor = () =>
    `rgb(${[...new Array(3)].map(() => 0 | (Math.random() * 256))})`

  onMount(() => {
    setInterval(() => {
      str = [...str, new Date()]
    }, 100)
  })
</script>

<svelte:head>
  <title>Tutorial B</title>
</svelte:head>

<div id="container" class="p-16 text-red-800">
  <h1 class="text-(center 8xl) line-height-relaxed">
    Let's go on a
    {#each str as s}
      <span
        style:color={rcolor()}
        style:-webkit-text-stroke="2px {rcolor()}"
        transition:fade
      >
        {' ' + s}
      </span>
    {/each}
  </h1>
</div>

<style>
  :root {
    @apply bg-pink-400;
  }

  #container {
    font-family: 'Comic Sans MS', 'Comic Sans', cursive, sans-serif;
  }
</style>

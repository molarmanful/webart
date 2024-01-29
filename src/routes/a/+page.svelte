<script>
  import { onMount } from 'svelte'

  let t
  let str =
    'my head is more empty than it should be at this approximate point in my meager lifespan...'
  $: fax = Object.entries(str)
  let rsz = [...str].map(() => 100)
  $: {
    t
    rsz = fax.map(() => Math.random())
  }

  onMount(() => {
    setInterval(() => {
      t = !t
    }, 200)
  })
</script>

<svelte:head>
  <title>Tutorial A</title>
</svelte:head>

<div
  id="container"
  class="screen bg-black text-black flex-(~ justify-center items-center) p-16"
>
  <h1 class="text-8xl line-height-relaxed text-justify">
    {#each fax as [i, c]}
      <span
        style:font-size="{rsz[i] * 100 + 50}%"
        class="transition-font-size duration-190">{c}</span
      >
    {/each}
  </h1>
</div>

<style>
  #container {
    font-family: 'Comic Sans MS', 'Comic Sans', cursive, sans-serif;
  }
</style>

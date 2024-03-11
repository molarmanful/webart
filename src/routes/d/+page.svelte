<script>
  import { onMount } from 'svelte'

  import { browser } from '$app/environment'

  let el
  let str = ''
  if (browser) str = new URL(location).searchParams.get('str') || ''

  onMount(() => {
    el.focus()
  })
</script>

<svelte:head>
  <title>{str || 'Tutorial D'}</title>
</svelte:head>

<div class="break-all">
  <textarea
    bind:this={el}
    class="min-h-screen min-w-screen"
    placeholder="type here to start..."
    on:input={() => {
      requestAnimationFrame(() => {
        location.href = '?str=' + encodeURIComponent(str)
      })
    }}
    bind:value={str}
  />
</div>

<style>
  :root {
    font-family: monospace;
  }
</style>

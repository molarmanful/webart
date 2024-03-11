<script>
  import { onMount } from 'svelte'

  import { page } from '$app/stores'

  let el
  let str = $page.url.searchParams.get('str') || ''

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
        location.href = '/d?str=' + encodeURIComponent(str)
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

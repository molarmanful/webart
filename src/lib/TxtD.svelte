<script>
  import { onMount } from 'svelte'

  export let el
  export let str = ''

  onMount(() => {
    el.focus()
  })
</script>

<textarea
  bind:this={el}
  class="min-h-screen min-w-screen"
  placeholder="type here to start..."
  on:input={() => {
    requestAnimationFrame(() => {
      location.href = '/d/' + encodeURIComponent(str)
    })
  }}
  bind:value={str}
/>

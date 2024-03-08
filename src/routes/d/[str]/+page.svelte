<script>
  import { page } from '$app/stores'
  import ContD from '$lib/ContD.svelte'
  import TxtD from '$lib/TxtD.svelte'

  let str = decodeURIComponent($page.params.str)
</script>

<svelte:head>
  <title>{str}</title>
</svelte:head>

<ContD>
  <TxtD {str} />
</ContD>

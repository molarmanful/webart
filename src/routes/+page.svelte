<script>
  let m = [
    ['./a', 'Tutorial A'],
    ['./b', 'Tutorial B'],
    ['./d', 'Tutorial D'],
    ['./e', 'Tutorial E'],
  ]
</script>

<svelte:head>
  <title>WEB ART STUFF</title>
</svelte:head>

<div class="screen flex flex-(justify-center items-center)">
  <div class="b-(1 black solid) p-16">
    <h1>CHICANERY</h1>
    <ul class="list-disc">
      {#each m as [href, text]}
        <li>
          <a class="text-blue underline" {href} target="_blank">{text}</a>
        </li>
      {/each}
    </ul>
  </div>
</div>

<style>
  :root {
    font-family: monospace;
  }
</style>

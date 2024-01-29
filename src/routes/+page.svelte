<script>
  let m = [['./a', 'Tutorial A']]
</script>

<div class="flex-(~ justify-center items-center) screen">
  <div class="p-16 b-(1 solid black)">
    <h1>CHICANERY</h1>
    <ul class="list-disc">
      {#each m as [href, text]}
        <li>
          <a {href} target="_blank" class="text-blue underline">{text}</a>
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

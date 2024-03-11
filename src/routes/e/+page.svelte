<script>
  import { faker } from '@faker-js/faker'
  import { onMount } from 'svelte'

  let iw = 0
  let loaded = false

  let randa = (n, m) => new Array(0 | (Math.random() * n + m))

  let randp = () => {
    let xs = [
      faker.company.catchPhrase() + '.',
      faker.company.buzzPhrase() + '.',
      faker.hacker.phrase(),
      faker.lorem.sentence(),
    ]
    return xs[0 | (Math.random() * xs.length)]
  }

  let randfnt = () => {
    let xs = [
      'Comic Sans MS',
      'Arial, sans-serif',
      'Verdana, sans-serif',
      'Tahoma, sans-serif',
      '"Trebuchet MS", sans-serif',
      '"Times New Roman", serif',
      'Georgia, serif',
      'Garamond, serif',
      '"Courier New", Courier, monospace',
      '"Brush Script MT", cursive',
    ]
    return xs[0 | (Math.random() * xs.length)]
  }

  let fsz = () => {
    for (let el of document.querySelectorAll('[data-factor]')) {
      el.style.fontSize = (iw / innerWidth) ** el.dataset.factor * 100 + '%'
    }
  }

  onMount(() => {
    for (let el of document.querySelectorAll('[sz]')) {
      let str = el.textContent
      el.textContent = ''
      for (let c of str) {
        let span = document.createElement('span')
        span.style.fontFamily = randfnt()
        span.dataset.factor = Math.random() * 4 - 2
        span.textContent = c
        el.append(span)
      }
    }
    iw = innerWidth
    fsz()
    loaded = true
  })
</script>

<svelte:head>
  <title>Tutorial E</title>
</svelte:head>

<svelte:window on:resize={fsz} />

<div
  class="{loaded
    ? 'opacity-100'
    : 'opacity-0'} m-auto max-w-prose transition-opacity-400"
>
  <h1 sz>{faker.company.buzzPhrase()}</h1>
  {#each randa(3, 3) as _}
    <h2 sz>{faker.company.name()}</h2>
    {#each randa(4, 2) as _}
      <p sz>
        {[...randa(9, 1)].map(randp).join` `}
      </p>
    {/each}
  {/each}
</div>

<style>
  :root {
    @apply uppercase p-8;
    font-family: 'Comic Sans MS';
  }

  :global([data-font]) {
    font-family: attr(data-font);
  }
</style>

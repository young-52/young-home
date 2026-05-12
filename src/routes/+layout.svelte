<script lang="ts">
import './layout.css'

let { children } = $props()
</script>

<svelte:head>
  <link
    rel="icon"
    href="data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'><text y='.9em' font-size='90'>👨‍💻</text></svg>"
  />
  <title>Junyoung Park | language, computer, and people</title>
  <meta
    name="description"
    content="Junyoung Park | language, computer, and people"
  />
</svelte:head>
<div class="flex min-h-svh w-full flex-col bg-[#f8f8f6] px-4 sm:px-6 lg:px-8">
  <main class="flex flex-1 flex-col">
    {@render children()}
  </main>
</div>

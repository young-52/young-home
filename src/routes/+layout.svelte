<script lang="ts">
import './layout.css'
import favicon from '$lib/assets/favicon.svg'

// biome-ignore lint: false positive
let { children } = $props()
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
	<title>Junyoung Park | language, computer, and people</title>
	<meta name="description" content="Junyoung Park | language, computer, and people" />
</svelte:head>
<div class="flex min-h-svh w-full flex-col bg-[#f8f8f6] px-4 sm:px-6 lg:px-8">
	<main class="flex flex-1 flex-col">
		{@render children()}
	</main>
</div>
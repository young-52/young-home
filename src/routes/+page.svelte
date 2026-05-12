<script lang="ts">
	import { FileText, Mail } from '@lucide/svelte';
	import profileImg from '$lib/assets/profile.jpg';
	import { Button } from '$lib/components/ui/button/index.js';
	import { news } from '$lib/data/news.js';

	let highlightTop = $state(0);
	let highlightHeight = $state(0);
	let highlightVisible = $state(false);

	function handleRowEnter(e: MouseEvent) {
		const row = e.currentTarget as HTMLElement;
		const container = row.closest('.news-rows') as HTMLElement;
		const containerRect = container.getBoundingClientRect();
		const rowRect = row.getBoundingClientRect();
		highlightTop = rowRect.top - containerRect.top;
		highlightHeight = rowRect.height;
		highlightVisible = true;
	}

	function handleContainerLeave() {
		highlightVisible = false;
	}
</script>

<section class="flex w-full items-center justify-center px-4 py-16 sm:px-0 sm:py-20">
	<div class="flex flex-col items-center gap-1 sm:flex-row sm:gap-8">
		<img
			src={profileImg}
			alt="Junyoung Park"
			class="size-28 rounded-full ring-2 ring-border sm:size-36 md:size-40"
		/>
		<div class="flex flex-col items-center justify-center gap-4 sm:items-start sm:gap-6">
			<div class="flex flex-col items-center justify-center gap-2 sm:items-start sm:gap-3">
				<span class="name-primary"><strong>PARK</strong> Junyoung</span>
				<span class="name-secondary">
					<strong class="font-semibold">/박준영/</strong> [pɐk̚ tɕu.nʲʌ̹ŋ]
				</span>
			</div>
			<div class="flex flex-wrap items-center justify-center gap-0.5 sm:justify-start">
				<span class="body-base text-[#79716b]">Undergraduate in Linguistics & CS @</span>
				<Button variant="link" href="https://snu.ac.kr" class="body-link px-0 font-normal">
					SNU
				</Button>
			</div>
		</div>
		<div class="flex justify-center gap-1 sm:justify-start">
			<Button
				variant="ghost"
				size="icon"
				href="mailto:bloomwayz@snu.ac.kr"
				title="Email"
				aria-label="Email"
				class="text-muted-foreground hover:text-foreground"
			>
				<Mail size={18} />
			</Button>
			<Button
				variant="ghost"
				size="icon"
				href="https://github.com/young-52"
				target="_blank"
				rel="noopener noreferrer"
				title="GitHub"
				aria-label="GitHub"
				class="text-muted-foreground hover:text-foreground"
			>
				<svg viewBox="0 0 16 16" width="18" height="18" fill="currentColor" aria-hidden="true">
					<path
						d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"
					/>
				</svg>
			</Button>
			<Button
				variant="ghost"
				size="icon"
				href="https://raw.githubusercontent.com/young-52/curriculum-vitae/main/cv-en.pdf"
				target="_blank"
				rel="noopener noreferrer"
				title="Curriculum Vitae"
				aria-label="Curriculum Vitae"
				class="text-muted-foreground hover:text-foreground"
			>
				<FileText size={18} />
			</Button>
		</div>
	</div>
</section>

<section class="mx-auto w-full max-w-2xl px-4 pb-16 sm:px-0">
	<h2 class="mb-4">Hi! 👋</h2>
	<div class="body-base flex flex-col gap-3">
		<p>
			I am interested in every area
			<strong class="font-semibold">where humans and computers meet</strong>. My goal is to improve
			developer experience based on natural/programming languages and HCI.
		</p>
		<p>
			Now, I am working as a research intern in
			<a
				href="https://knlp.snu.ac.kr"
				class="text-primary underline-offset-4 transition-all hover:underline">SNUNLP Lab</a
			>. I recently focus on interpretability of LLMs for code generation.
		</p>
	</div>
</section>

<section class="mx-auto w-full max-w-2xl px-4 pb-16 sm:px-0">
	<h2>Recent News</h2>
	<div class="news-rows relative mt-3" onmouseleave={handleContainerLeave} role="table">
		<div
			class="highlight pointer-events-none absolute inset-x-0 rounded-md bg-muted"
			style="top: {highlightTop}px; height: {highlightHeight}px; opacity: {highlightVisible
				? 1
				: 0};"
		></div>
		{#each news as item (item.headline)}
			<div
				class="relative grid grid-cols-[7rem_1fr] gap-4 px-3 py-2"
				onmouseenter={handleRowEnter}
				role="row"
				tabindex="0"
			>
				<span class="news-date text-muted-foreground">{item.date}</span>
				<span class="news-headline">{item.headline}</span>
			</div>
		{/each}
	</div>
</section>

<style>
	.name-primary {
		font-family: 'Hedvig Letters Serif', serif;
		font-size: clamp(1.5rem, 4vw + 0.5rem, 2.25rem);
		font-style: normal;
		line-height: 120%;
	}

	.name-secondary {
		font-size: clamp(0.875rem, 2vw + 0.25rem, 1.125rem);
		font-style: normal;
		line-height: 120%;
	}

	.body-base {
		font-size: clamp(0.8125rem, 1.5vw + 0.25rem, 1rem);
		font-style: normal;
		font-weight: 400;
		line-height: 170%;
	}

	/* Suppress warning `css_unused_selector` */
	:global(.body-link) {
		font-size: clamp(0.8125rem, 1.5vw + 0.25rem, 1rem);
	}

	h2 {
		font-family: 'Hedvig Letters Serif', serif;
		font-size: clamp(1rem, 2vw + 0.25rem, 1.25rem);
		font-weight: 600;
		line-height: 120%;
	}

	.news-date {
		font-size: 0.875rem;
		line-height: 1.5;
		white-space: nowrap;
	}

	.news-headline {
		font-size: 0.875rem;
		line-height: 1.5;
	}

	.highlight {
		transition:
			top 150ms ease,
			height 150ms ease,
			opacity 100ms ease;
	}
</style>

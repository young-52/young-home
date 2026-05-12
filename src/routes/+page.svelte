<script lang="ts">
import profileImg from '$lib/assets/profile.jpg'
import { Button } from '$lib/components/ui/button/index.js'
import { news } from '$lib/data/news.js'

// biome-ignore lint:noUnusedVariables
let highlightTop = $state(0)
// biome-ignore lint:noUnusedVariables
let highlightHeight = $state(0)
// biome-ignore lint:noUnusedVariables
let highlightVisible = $state(false)

// biome-ignore lint:noUnusedVariables
function handleRowEnter(e: MouseEvent) {
  const row = e.currentTarget as HTMLElement
  const container = row.closest('.news-rows') as HTMLElement
  const containerRect = container.getBoundingClientRect()
  const rowRect = row.getBoundingClientRect()
  highlightTop = rowRect.top - containerRect.top
  highlightHeight = rowRect.height
  highlightVisible = true
}

// biome-ignore lint:noUnusedVariables
function handleContainerLeave() {
  highlightVisible = false
}
</script>

<div class="flex w-full justify-center items-center py-16 sm:py-20 px-4 sm:px-0">
  <div class="flex flex-col sm:flex-row items-center gap-5 sm:gap-8">
    <img
      src={profileImg}
      alt="Junyoung Park"
      class="rounded-full size-28 sm:size-36 md:size-40"
    />
    <div class="flex flex-col justify-center items-center sm:items-start gap-4 sm:gap-6">
      <div class="flex flex-col gap-2 sm:gap-3 justify-center items-center sm:items-start">
        <span class="name-primary"><strong>PARK</strong> Junyoung</span>
        <span class="name-secondary">
          <strong class="font-semibold">/박준영/</strong> [pɐk̚ tɕu.nʲʌ̹ŋ]
        </span>
      </div>
      <div class="flex flex-wrap gap-0.5 items-center justify-center sm:justify-start">
        <span class="body-base">Studying Linguistics & Computer Science at</span>
        <Button
          variant="link"
          href="https://snu.ac.kr"
          class="body-link font-normal px-0"
        >
          SNU
        </Button>
      </div>
    </div>
  </div>
</div>

<section class="w-full max-w-2xl mx-auto px-4 sm:px-0 pb-16">
  <h2 class="section-title">Recent News</h2>
  <div
    class="news-rows relative mt-3"
    onmouseleave={handleContainerLeave}
    role="table"
  >
    <div
      class="highlight absolute inset-x-0 bg-muted rounded-md pointer-events-none"
      style="top: {highlightTop}px; height: {highlightHeight}px; opacity: {highlightVisible ? 1 : 0};"
    ></div>
    {#each news as item}
      <div
        class="relative grid grid-cols-[9rem_1fr] gap-4 px-3 py-2"
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
    font-family: "Hedvig Letters Serif", serif;
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
    color: #79716b;
    font-size: clamp(0.8125rem, 1.5vw + 0.25rem, 1rem);
    font-style: normal;
    font-weight: 400;
    line-height: 120%;
  }

  /* Suppress warning `css_unused_selector` */
  :global(.body-link) {
    font-size: clamp(0.8125rem, 1.5vw + 0.25rem, 1rem);
  }

  .section-title {
    font-family: "Hedvig Letters Serif", serif;
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
    transition: top 150ms ease, height 150ms ease, opacity 100ms ease;
  }
</style>

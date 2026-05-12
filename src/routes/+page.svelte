<script>
import profileImg from '$lib/assets/profile.jpg'
import { Button } from '$lib/components/ui/button/index.js'
</script>

<div class="flex flex-1 w-full justify-center items-center px-4 sm:px-0">
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
</style>

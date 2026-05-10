<script>
import profileImg from '$lib/assets/profile.jpg'
import { Button } from '$lib/components/ui/button/index.js'
</script>

<div class="flex flex-1 w-full justify-center">
  <div class="flex items-center gap-8">
    <img src={profileImg} alt="Junyoung Park" class="rounded-full size-40" />
    <div class="flex flex-col justify-center gap-6">
      <div class="flex flex-col gap-3 justify-center">
        <span class="name-primary"><strong>PARK</strong> Junyoung</span>
        <span class="name-secondary">
          <strong class="font-semibold">/박준영/</strong> [pɐk̚ tɕu.nʲʌ̹ŋ]
        </span>
      </div>
      <div class="flex gap-1 items-center">
        <span class="body-base">Studying Linguistics & Computer Science at</span
        >
        <Button
          variant="link"
          href="https://snu.ac.kr"
          class="text-[18px] font-normal px-0"
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
    font-size: 36px;
    font-style: normal;
    line-height: 120%;
  }

  .name-secondary {
    font-size: 18px;
    font-style: normal;
    line-height: 120%;
  }

  .body-base {
    color: #79716b;
    font-size: 16px;
    font-style: normal;
    font-weight: 400;
    line-height: 120%;
  }
</style>

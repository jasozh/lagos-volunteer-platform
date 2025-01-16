<script lang="ts">
  let {
    images,
  }: {
    images: { src: string; alt?: string; header?: string; label?: string }[];
  } = $props();

  /**
   * A number array of the current slides in the carousel
   *
   * Examples:
   * - If images = [0 1 2 3 4], then slides = [3 4|0 1 2 3 4|0 1].
   * - If images = [0 1 2], then slides = [1 2|0 1 2|0 1].
   * - If images = [0 1], then slides = [0 1|0 1|0 1].
   *
   * If you are at 0 and want to move left, you are teleported to the rightmost
   * 0 before the left slide occurs. If you are at 4 and want to move right, you
   * are teleported to the leftmost 4.
   */
  let slides = $state(
    [images.length - 2, images.length - 1].concat(
      images.map((img, i) => i),
      [0, 1],
    ),
  );

  /** The current position in the slides, unrelated to the actual image index */
  let position = $state(2);

  let curr = $state(0);
  let prev = $derived(curr > 0 ? curr - 1 : images.length - 1);
  let next = $derived(curr < images.length - 1 ? curr + 1 : 0);

  function changeSlide(slideTarget: number) {
    let [fakeLastPosition, realLastPosition] = [1, slides.length - 3];
    let [fakeFirstPosition, realFirstPosition] = [slides.length - 2, 2];

    // Do teleportation if needed
    if (position === realLastPosition && slideTarget === next) {
      position = fakeLastPosition;
      position++;
    } else if (position === realFirstPosition && slideTarget === prev) {
      position = fakeFirstPosition;
      position--;
    } else {
      position = slideTarget + 2;
    }

    curr = slideTarget;

    clearInterval(autoSlide);
    autoSlide = setInterval(showNext, 8000);
  }

  function showNext() {
    return changeSlide(next);
  }

  // let autoSlide = setInterval(showNext, 8000);
</script>

<div class="relative w-full">
  <!-- Carousel -->
  <div class="relative">
    <div
      class="relative h-[720px] w-screen overflow-hidden"
      style="left: calc(-50vw + 50%);"
    >
      {#each slides as imageIndex, slidePosition}
        {@const translatePercent = 100 * (slidePosition - position)}
        {@const translateConstant = 96 * (slidePosition - position)}
        <div
          class="absolute inset-0 mx-auto max-w-screen-xl overflow-hidden rounded-lg duration-700 ease-in-out"
          style="transform: translateX(calc({translatePercent}% + {translateConstant}px));"
        >
          <img
            src={images[imageIndex].src}
            class="absolute left-1/2 top-1/2 block w-full -translate-x-1/2 -translate-y-1/2"
            alt={images[imageIndex].alt}
          />
        </div>
      {/each}
    </div>
  </div>

  <!-- Slider indicators -->
  <div class="flex">
    <div class="mx-auto flex space-x-3 py-9 rtl:space-x-reverse">
      {#each images as img, i}
        {@const bg = curr === i ? "bg-gray-900" : "bg-gray-300"}
        <button
          type="button"
          onclick={(event) => changeSlide(i)}
          class="h-3 w-3 rounded-full {bg}"
          aria-current={curr === i ? "true" : "false"}
          aria-label="Slide {i}"
        ></button>
      {/each}
    </div>
  </div>

  <!-- Labels -->
  {#each images as img, i}
    {#if curr === i && img.header}
      <div class="mb-2">
        <b>{img.header}</b>
      </div>
    {/if}
    {#if curr === i && img.label}
      <p>{img.label}</p>
    {/if}
  {/each}
</div>

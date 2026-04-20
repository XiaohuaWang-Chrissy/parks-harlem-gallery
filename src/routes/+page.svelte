<script>
  import SlideGallery from '$lib/components/MultimediaGallery/SlideGallery.svelte';
  import TitleSlide from '$lib/components/MultimediaGallery/TitleSlide.svelte';
  import PhotoSlide from '$lib/components/MultimediaGallery/PhotoSlide.svelte';
  import TextSlide from '$lib/components/MultimediaGallery/TextSlide.svelte';
  import CreditsSlide from '$lib/components/MultimediaGallery/CreditsSlide.svelte';

  let { data } = $props();
</script>

<SlideGallery>
  <TitleSlide
    headline="Picking Up the Pieces in Western North Carolina"
    intro="After Hurricane Helene tore through western North Carolina, residents faced the long, painful work of rebuilding their lives."
    byline="Photos by Chrissy Wang"
  />

  {#each data.story as slide (slide.id)}
    {#if slide.type === 'photo'}
      <PhotoSlide photo={slide} />
    {:else if slide.type === 'text'}
      <TextSlide {slide} />
    {/if}
  {/each}

  <CreditsSlide>
    <h2>About This Story</h2>
    <p>
      Xiaohua (Chrissy) Wang reported and photographed this story in October 2024, visiting
      Swannanoa, Marion, and Saluda, N.C., in the weeks after Hurricane Helene made landfall.
    </p>
    <p>
      This story was originally published by
      <a href="https://mediahub.unc.edu/picking-up-the-pieces-in-western-north-carolina/" target="_blank">
        UNC MediaHub</a> on Dec. 2, 2024.
    </p>
  </CreditsSlide>
</SlideGallery>
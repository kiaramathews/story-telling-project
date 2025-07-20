<script>
  import { onMount } from 'svelte';

  let scrollY = 0;

  const delayStart = 900;  // delay zoom until 300px of scroll
  const zoomDuration = 800; // zoom completes after another 600px
  const maxZoom = 2;

  // Track scroll position
  onMount(() => {
    const onScroll = () => {
      scrollY = window.scrollY;
    };
    window.addEventListener('scroll', onScroll);
    return () => window.removeEventListener('scroll', onScroll);
  });

  // Calculate zoom (starts after delayStart)
  $: zoomProgress = Math.max(scrollY - delayStart, 0);
  $: zoomRatio = Math.min(zoomProgress / zoomDuration, 1);
  $: zoomScale = 1 + zoomRatio * (maxZoom - 1);
</script>

<style>
  .scroller-section {
    display: flex;
    min-height: 300vh; /* More height = more scroll */
    background-color: #a71c1c;
  }

  .image-container {
    position: sticky;
    top: 0;
    height: 100vh;
    width: 50vw;
    overflow: hidden;
    background-color: #000;
  }

  .zoom-image {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transition: transform 0.1s linear;
    will-change: transform;
    transform-origin: top left
  }

  .text-content {
    width: 50vw;
    padding: 4rem 2rem;
   background-color: #ac1e1e;
   padding: 2rem;

 
  }

  .text-block {
    margin-bottom: 80vh; /* creates scroll distance */
       box-sizing: border-box;
   font-family: 'Playfair Display', serif;
  }
</style>

<div class="scroller-section">
  <div class="image-container">
    <img
      src="https://i.postimg.cc/43hL6XX2/d22d769c-043f-46b4-b7ff-be7f1d8e8bb7.png"
      alt="Zooming Image"
      class="zoom-image"
      style="transform: scale({zoomScale});"
    />
  </div>

  <div class="text-content">
    <div class="text-block">
      <h2>Welcome</h2>
      <p>Image is visible and sticky. Zoom won't start yet.</p>
    </div>
    <div class="text-block">
      <h2>Keep Scrolling</h2>
      <p>Now you're entering the zoom range. Watch it grow.</p>
    </div>
    <div class="text-block">
      <h2>Zoom Complete</h2>
      <p>Zoom has finished. Image starts to scroll away now.</p>
    </div>
  </div>
</div>

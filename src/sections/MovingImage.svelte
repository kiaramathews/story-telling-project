<script>
  import { onMount, onDestroy } from 'svelte';

  const images = [
    'https://i.imgur.com/TF0lTNs.png',
    'https://i.imgur.com/sPia0Ii.png',
    'https://i.imgur.com/pX2dVpd.png',
    'https://i.imgur.com/pC5gEjQ.png',
    'https://i.imgur.com/lJoOI3l.png'
  ];

  let current = 0;
  let currentImage = images[current];
  let interval;

  onMount(() => {
    interval = setInterval(() => {
      current = (current + 1) % images.length;
      currentImage = images[current];
    }, 1000);
  });

  onDestroy(() => {
    clearInterval(interval);
  });
</script>

<style>
  .slideshow-container {
    position: relative;
    width: 100%;
    height: auto;
  }

  .center-text {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    font-size: 4rem;
    font-weight: bold;
    color: white;
    text-shadow: 2px 2px 8px rgba(0, 0, 0, 0.7);
    pointer-events: none;
    font-family: 'Playfair Display', serif;
    
  }

</style>

<div class="slideshow-container">
  <img src="{currentImage}" alt="Slideshow" style="width: 100%; height: auto;" />
  <div class="center-text">Statistics</div>
</div>

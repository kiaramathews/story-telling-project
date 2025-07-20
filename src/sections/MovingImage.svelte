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

<img src="{currentImage}" alt="Slideshow" style="width: 100%; height: auto;" />

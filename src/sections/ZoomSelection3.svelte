<script>
  import { onMount } from 'svelte';

  let scrollY = 0;

  const delayStart = 6000;  
  const zoomDuration = 800; 
  const maxZoom = 1.2;


  onMount(() => {
    const onScroll = () => {
      scrollY = window.scrollY;
    };
    window.addEventListener('scroll', onScroll);
    return () => window.removeEventListener('scroll', onScroll);
  });

  $: zoomProgress = Math.max(scrollY - delayStart, 0);
  $: zoomRatio = Math.min(zoomProgress / zoomDuration, 1);
  $: zoomScale = 1 + zoomRatio * (maxZoom - 1);
</script>

<style>
  .scroller-section {
    display: flex;
    min-height: 300vh; 
    background-color: #050505;
  }

  .image-container {
    position: sticky;
    top: 0;
    height: 100vh;
    width: 50vw;
    overflow: hidden;
    background-color: #030202;
     padding-top: 0.3rem;
  }

  .zoom-image {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transition: transform 0.1s linear;
    will-change: transform;
  }

  .text-content {
    width: 50vw;
    padding: 4rem 2rem;
   background-color: #000000;
   padding: 2rem;

 
  }

  .text-block {
    margin-bottom: 40vh;
       box-sizing: border-box;
   font-family: 'Playfair Display', serif;
   color: white;
  }
  .image-block{
    object-fit: cover;
  width: 100%;
  height: 80vh; 
  overflow: hidden;
  margin-bottom: 30vh;
  border-radius: 20px;
  }
    .header-style{
    font-size: 2rem;
  }
    .body-style{
    font-size: 1.8rem;
  }
</style>

<div class="scroller-section">
  <div class="image-container">
    <img
      src="https://i0.wp.com/whatbeautifullight.com/wp-content/uploads/2016/06/apartments-used-and-empty.jpg?w=4000&h=&ssl=1"
      alt="Zooming Image"
      class="zoom-image"
      style="transform: scale({zoomScale});"
    />
  </div>

  <div class="text-content">
    <div class="text-block">
        <div class="header-style">
      <h2>"In 1916, St. Louisans voted on a “reform” ordinance that would prevent anyone from buying a home in a neighborhood more than 75 percent occupied by another race.""</h2>
      </div>
        <div class="body-style">
      <p>The </p>
      </div>
    </div>
    <div class="image-block">
        <img src="https://www.tba.org/userassets/TNBAR/TNBAR/userimages/fowlerrussell_redlining_janfeb22_final-4.jpg"/>
    </div>
    <div class="text-block">
        <div class="header-style">
      <h2>Keep Scrolling</h2>
      </div>
      <div class="body-style">
      <p>Now you're entering the zoom range. Watch it grow.</p>
      </div>
    </div>
    <div class="image-block">
        <img src="https://www.epi.org/files/2014/st-louis-1942-protests.png">
    </div>
    <div class="text-block">
        <div class="header-style">
      <h2>Zoom Complete</h2>
      </div>
      <div class="body-style">
      <p>Zoom has finished. Image starts to scroll away now.</p>
      </div>
    </div>
  </div>
</div>

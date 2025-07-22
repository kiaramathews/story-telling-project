<script>
  import { onMount } from 'svelte';

  let scrollY = 0;

  const delayStart = 9000;  
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
  height: 70vh; 
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

  <div class="text-content">
    <div class="text-block">
        <div class="header-style">
      <h2>The Delmar Divide: In St. Louis, the HOLC maps created what is now known as “the Delmar Divide.” </h2>
    </div>  
        <div class="body-style">
      <p> The map that divded in the neighborhood of Delmar, effectively ensured that all Black people would be required to live north of Delmar boulevard and all the White people would live south. This act had lasting affects on St. Louis and to this day it still remains a segregated city due to these early policies.</p>
    </div>
    </div>
    <div class="image-block">
        <img src="https://richmondstandard.com/wp-content/uploads/2023/04/JimCrowMustGo.jpg"/>
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
      <div class="image-container">
    <img
      src="https://i.postimg.cc/WbSLd7FS/Screenshot-2025-07-21-at-12-11-12-PM.png"
      alt="Zooming Image"
      class="zoom-image"
      style="transform: scale({zoomScale});"
    />
  </div>
  </div>

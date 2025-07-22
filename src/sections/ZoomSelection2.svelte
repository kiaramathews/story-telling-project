<script>
  import { onMount } from 'svelte';

  let scrollY = 0;

  const delayStart = 3500;  
  const zoomDuration = 1000; 
  const maxZoom = 2;


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
    background-color: #f0f0f0;
  }

  .image-container {
    position: sticky;
    top: 0;
    height: 100vh;
    width: 50vw;
    overflow: hidden;
    background-color: #000;
     padding-bottom: 0.5rem;
  }

  .zoom-image2 {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transition: transform 0.1s linear;
    will-change: transform;
    transform-origin: bottom right;
  }

  .text-content {
    width: 50vw;
    padding: 4rem 2rem;
    background: #090909
  }

  .text-block {
    margin-bottom: 20vh;
    box-sizing: border-box;
   font-family: 'Playfair Display', serif;
   color: white;
  }
    .header-style{
    font-size: 2rem;
  }
    .body-style{
    font-size: 0.8rem;
  }
    .body-style2{
    font-size: 1.8rem;
}
  .image-block-img {
  width: 100%;
  height: 50vh; 
  overflow: hidden;
  margin-bottom: 20vh;
  border-radius: 20px;
}

.image-block-img img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
}
</style>

<div class="scroller-section">

  <div class="text-content">
    <div class="text-block">
        <div class="header-style">
      <h2>“Redlining limitations led entire neighborhoods to fall economically, declining property values and isolation from essential services."</h2>
        </div>
        <div class="body-style2">
      <p>The isolation that black households were under restricted their access to schools, retail and grocery stores, public transportation, and public services. Redlining also reinforced and enabled acts of discrimination and inequality due to the division between the communities. </p>
      </div>
    </div>
        <div class="image-block-img">
        <img src="https://fairhousingnj.org/wp-content/uploads/2019/07/LBJ-signing-2-768x521-1.jpg"/>
        </div>
    <div class="text-block">
        <div class="header-style">
      <h2>Redlining Abolished: In 1968 "The Fair Housing Act" prohibited discrimination in housing based on color, race, national origin, religion, sex, familial status, or disability.</h2>
      </div>
        <div class="body-style2">
      <p>This act made it illeagl for anyone to deny any person housing. It also protects people with these characteristics to be treated fairly when renting, selling, or buying housing.</p>
      </div>
    </div>
  </div>

    <div class="image-container">
    <img
      src="https://i.postimg.cc/Ghdm6pNY/Screenshot-2025-07-20-at-12-19-52-AM.png"
      alt="Zooming Image"
      class="zoom-image2"
      style="transform: scale({zoomScale});"
    />
  </div>
</div>

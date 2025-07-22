<script>
  import { onMount } from 'svelte';

  let scrollY = 0;

  const delayStart = 1000;  
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
    transition: transform 0.3s linear;
    will-change: transform;
    transform-origin: top left
  }

  .text-content {
    width: 50vw;
    padding: 4rem 2rem;
   background-color: #000000;
   padding: 2rem;

 
  }

  .text-block {
    margin-bottom: 30vh;
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
  margin-bottom: 30vh;
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
        <div class="header-style">
      <h2>“Redlining: a phrase that described the color coding system developed by the Home Owners’ Loan Corporation (HOLC)"</h2>
        </div>
        <div class="body-style">
      <p>Brizee, Stephanie. “1935: More Red: Redlining and Segregated Housing.” The Saint Louis Story, 18 Sept. n.d., www.thesaintlouisstory.org/history-1/1935-redlining. Accessed 21 July 2025.</p>
        </div>
        <div class="body-style2">
      <p>It became one of most impacting means of enforcing Black segregation in the housing market and weakened the African American generational wealth development.</p>
      </div>
    </div>
        <div class="image-block-img">
        <img src="https://i.postimg.cc/y8zRjd9r/Screenshot-2025-07-21-at-6-47-28-PM.png"/>
        </div>
    <div class="text-block">
        <div class="header-style">
      <h2>Where the term “redlining” came from: it was created in 1930s to help refinance homes during the Great Depression</h2>
      </div>
        <div class="body-style2">
      <p>The federal government established the Home Owners’ Loan Corporation to help refinance households after the Great Depression. In doing so, the program created maps that graded American cities to help banks and lenders know which cities were more likely to pay back the money, and which were “high-risk”. The lowest grades mostly went to cities with high populations of African Americans and other people of color, making it extremely hard for households in these communities to obtain financial services. </p>
      </div>
    </div>
  </div>
</div>

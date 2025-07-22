<script>
   export let title;
   export let subtitle;
   export let scrollY = 0;

   $: fadeAmount = Math.min(scrollY / 75, 1); 
   $: contentOpacity = 1 - fadeAmount;
   $: bg1Opacity = 1 - fadeAmount;
   $: bg2Opacity = fadeAmount;
</script>

<div class="title-card">

   <div class="bg-layer bg1" style="opacity: {bg1Opacity}"></div>
   <div class="bg-layer bg2" style="opacity: {bg2Opacity}"></div>


   <div class="content" style="opacity: {contentOpacity}">
       <h1>{title}</h1>
       <p>{subtitle}</p>
   </div>
</div>

<style>
.title-card {
   position: relative;
   height: 100vh;
   overflow: hidden;
   display: flex;
   justify-content: center;
   align-items: center;
   text-align: center;
   padding: 2rem;
   box-sizing: border-box;
   font-family: 'Playfair Display', serif;
}


.bg-layer {
   position: absolute;
   top: 0;
   left: 0;
   width: 100%;
   height: 100%;
   background-size: cover;
   background-position: center;
   transition: opacity 0.5s ease;
   z-index: 0;
   padding-bottom: 2rem;
}

.bg1 {
   background-image: url('https://i.postimg.cc/vHSYSvdg/Untitled-design-14.png');
}

.bg2 {
   background-image: url('https://i.postimg.cc/h4sPVBy0/Untitled-design-13.png'); 
}


.content {
   position: relative;
   bottom: 7rem; 
   z-index: 1;
   max-width: 400px;
   padding: 2rem;
   transition: opacity 1.5s ease-out;
}

h1 {
   font-size: 4rem;
   margin: 0;
   color: #000000;
   text-shadow: 3px 1px 0 #b3b3b3;
}

p {
   font-size: 1.3rem;
   color: #f7f5eb;
   margin-top: 1rem;
}

@media (max-width: 600px) {
   h1 {
       font-size: 2.2rem;
   }
   p {
       font-size: 1.1rem;
   }
}
</style>

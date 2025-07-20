<script>
   export let title;
   export let subtitle;
   export let scrollY = 0;

   // Scroll-based fading logic
   $: fadeAmount = Math.min(scrollY / 100, 1); // from 0 to 1
   $: contentOpacity = 1 - fadeAmount;
   $: bg1Opacity = 1 - fadeAmount;
   $: bg2Opacity = fadeAmount;
</script>

<div class="title-card">
   <!-- Background image layers -->
   <div class="bg-layer bg1" style="opacity: {bg1Opacity}"></div>
   <div class="bg-layer bg2" style="opacity: {bg2Opacity}"></div>

   <!-- Text content -->
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

/* Background image layers */
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
}

.bg1 {
   background-image: url('https://i.postimg.cc/vHSYSvdg/Untitled-design-14.png');
}

.bg2 {
   background-image: url('https://i.postimg.cc/h4sPVBy0/Untitled-design-13.png'); /* 🔁 Your new image */
}

/* Text content block */
.content {
   position: relative;
   z-index: 1;
   max-width: 700px;
   background-color: #c3c2c2;
   padding: 2rem;
   border: 1px solid #010101;
   box-shadow: 16px 16px #971924;
   transition: opacity 0.3s ease-out;
}

h1 {
   font-size: 3rem;
   margin: 0;
   color: #070202;
   text-shadow: 3px 1px 0 #807b7b;
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

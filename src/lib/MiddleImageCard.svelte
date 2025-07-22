<script>
   export let title;
   export let subtitle;
   export let scrollY = 0;

 const fadeStart = 5500; 
const fadeDuration = 300; 

$: fadeAmount = Math.min(Math.max((scrollY - fadeStart) / fadeDuration, 0), 1);
 
   $: contentOpacity = 1 - fadeAmount;
   $: bg1Opacity = 1 - fadeAmount;
   $: bg2Opacity = fadeAmount;
</script>

<div class="title-card">
   <div class="bg-layer bg3" style="opacity: {bg1Opacity}"></div>
   <div class="bg-layer bg4" style="opacity: {bg2Opacity}"></div>


   <div class="content">
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
   top: 2 rem;
   left: 0;
   width: 100%;
   height: 150%;
   background-size: cover;
   background-position: center;
   transition: opacity 0.5s ease;
   z-index: 0;
}

.bg3 {
   background-image: url('https://i.postimg.cc/pV45LzSb/Untitled-design-16.png');
}

.bg4 {
   background-image: url('https://i.postimg.cc/NF3KCvXf/Untitled-design-15.png'); 
}


.content {
   position: absolute;
   top: 5rem;        
   left: 50%;
   transform: translateX(-50%);
   z-index: 1;
   max-width: 600px;

}


h1 {
   font-size: 6rem;
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

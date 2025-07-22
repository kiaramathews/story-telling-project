<script>
   import { onMount } from "svelte";
   import TitleCard from "../lib/MiddleImageCard.svelte";

   const title = "REDLINING IN ST. LOUIS";
   const subtitle = "Discover how redlining directly impacted the city of St. Louis ";

   let scrollY = 0;

   const handleScroll = () => {
      scrollY = window.scrollY;
   };

   onMount(() => {
      window.addEventListener("scroll", handleScroll);
      return () => window.removeEventListener("scroll", handleScroll);
   });
</script>

<TitleCard {title} {subtitle} {scrollY} />
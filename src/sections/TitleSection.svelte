<script>
   import { onMount } from "svelte";
   import TitleCard from "../lib/TitleCard.svelte";

   const title = "THE IMPACT OF REDLINING";
   const subtitle = "Follow the journey on how racially motivated housing boarders that have founded the economic world we live in today.";

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

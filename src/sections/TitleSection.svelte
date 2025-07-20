<script>
   import { onMount } from "svelte";
   import TitleCard from "../lib/TitleCard.svelte";

   const title = "The Impact of Red-Lining";
   const subtitle = "A journey through data, creativity, and code";

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

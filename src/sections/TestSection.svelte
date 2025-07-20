<script>
  import Scroller from '../lib/Scroller.svelte';
  import ArticleText from '../lib/ArticleText.svelte';
</script>

<div>
    <Scroller layout="left">
        {#snippet sticky()}
         <img src="https://hips.hearstapps.com/hmg-prod/images/taylor-swift-performs-onstage-during-taylor-swift-the-news-photo-1733447389.jpg?crop=0.65234xw:1xh;center,top&resize=640:*" alt="Example chart" style="width: 100%;" />
        
     {/snippet}

        {#snippet scrolly()}
        <ArticleText>
             <h2>Scroll-triggered content</h2>
        <p>This content appears as you scroll through the section.</p>
        </ArticleText>
        {/snippet}
    </Scroller>

</div>
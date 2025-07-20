<script>
    import Scroller from "../lib/Scroller.svelte";
    import ArticleText from "../lib/ArticleText.svelte";

</script>

<div>
    <Scroller layout="right">
        {#snippet scrolly()}
            <ArticleText>
                <img src="https://i.pinimg.com/736x/77/43/4a/77434ae16d68c50132c91120e746e725.jpg" 
                    alt="Red Line Example" 
                    style="max-width: 100%; height: auto; display: block; margin: 0 auto;" 
                />
            </ArticleText>
        {/snippet}
    </Scroller>
</div>





 



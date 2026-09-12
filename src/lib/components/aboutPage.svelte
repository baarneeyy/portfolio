<script lang="ts">
    import InfoCard from "$lib/components/infoCard.svelte";
    import IntroText from "$lib/blog/introText.svx";
    import AboutText from "$lib/blog/aboutText.svx"

    import { fade } from "svelte/transition";
    let showIntro: boolean = $state(true);
</script>
<div class="container" onclick={() => {showIntro = !showIntro}}>
    {#key showIntro}
        <div class="markdown-content prose" in:fade={{ duration:500 }}>
            {#if showIntro}    
                <IntroText />
            {:else}
                <AboutText />
            {/if}
        </div>
    {/key}
</div>

<style>
    .container {
        user-select: none;
        min-height: 100%;
        display: flex;
        flex-direction: column;
        font-size: x-large;
        align-items: center;
        justify-content: center;
        cursor: pointer;
    }
</style>

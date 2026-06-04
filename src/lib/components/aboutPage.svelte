<script lang="ts">
    import InfoCard from "$lib/components/infoCard.svelte";
    import IntroText from "$lib/blog/introText.svx";
    import AboutText from "$lib/blog/aboutText.svx"

    let showIntro: boolean = $state(true);
</script>
<div class="container" onclick={() => {showIntro = !showIntro}}>
    {#if showIntro}
        <div class="markdown-content">
            <IntroText />
        </div>
    {:else}
        <div class="markdown-content">
            <AboutText />
        </div>
    {/if}
</div>

<style>
    .container {
        min-height: 100%;
        display: flex;
        flex-direction: column;
        font-size: x-large;
        align-items: center;
        justify-content: center;
    }
</style>

<script>
    import InfoCard from "$lib/components/infoCard.svelte";
    import AboutText from "$lib/blog/aboutText.svx";
</script>
<div class="container">
    <AboutText />
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
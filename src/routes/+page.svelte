<script lang="ts">
    import Section from "$lib/components/section.svelte";

    let expandedSection = $state<number | null>(0);

    function toggle(id: number) {
        expandedSection = expandedSection === id ? null : id;
    }
</script>

<div class="section-carousel">
    <Section sectionId={0} {expandedSection} onSelect={toggle} />
    <Section sectionId={1} {expandedSection} onSelect={toggle} />
    <Section sectionId={2} {expandedSection} onSelect={toggle} />
</div>

<style>
    .section-carousel {
        display: flex;
        flex-direction: row;
        height: 100vh;
        width: 100%;
    }
</style>

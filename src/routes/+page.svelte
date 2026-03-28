<script lang="ts">
    import Section from "$lib/components/section.svelte";

    let expandedSection = $state<number | null>(0);

    function toggle(id: number) {
        expandedSection = expandedSection === id ? null : id;
    }
</script>

<div class="section-carousel">
    <Section 
        sectionId={0} 
        {expandedSection} 
        onSelect={toggle} 
        sectionName="Myself"
        contentType="info"
    />
    <Section 
        sectionId={1} 
        {expandedSection} 
        onSelect={toggle} 
        sectionName="Experience & Education"
        contentType="timeline"
    />
    <Section 
        sectionId={2} 
        {expandedSection} 
        onSelect={toggle} 
        sectionName="Projects"
        contentType="projects"
    />
</div>

<style>
    .section-carousel {
        display: flex;
        flex-direction: row;
        min-height: 100vh;
        width: 100%;
    }
</style>

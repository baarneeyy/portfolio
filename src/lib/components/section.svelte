<script lang="ts">
    import AboutPage from "$lib/components/aboutPage.svelte";
    import GraphCard from "$lib/components/graphCard.svelte";
    import ProjectPage from "$lib/components/projectPage.svelte";

    let { sectionId, expandedSection, onSelect, sectionName, contentType }: {
        sectionId: number;
        expandedSection: number | null;
        onSelect: (id: number) => void;
        sectionName: string;
        contentType: string;
    } = $props();

    let isExpanded = $derived(expandedSection === sectionId);
</script>

<div class="section" class:expanded={isExpanded} onclick={() => { if (!isExpanded) onSelect(sectionId); }}>
    <button class="title" onclick={() => onSelect(sectionId)}>
        {sectionName}
    </button>
    <div class="content">
        {#if contentType == "projects"}
            <ProjectPage />
        {:else if contentType == "info"}
            <AboutPage />
        {:else}
            <p>Education</p>
            <GraphCard />
        {/if}
    </div>
</div>

<style>
    .section {
        display: flex;
        flex-direction: row;
        flex: 1;
        min-width: 3rem;
        overflow: hidden;
        transition: flex 0.45s cubic-bezier(0.4, 0, 0.2, 1);
        border-right: 2px solid #e5e7eb;
    }
    .section:last-child {
        border-right: none;
    }
    .section.expanded {
        flex: 5;
    }
    .title {
        writing-mode: vertical-lr;
        text-orientation: mixed;
        padding: 1rem 0.75rem;
        cursor: pointer;
        flex-shrink: 0;
        background: none;
        border: none;
        font-size: 0.9rem;
        font-weight: 600;
        letter-spacing: 0.05em;
        white-space: nowrap;
        transition: color 0.2s ease;
    }
    .content {
        flex: 1;
        padding: 1.5rem;
        overflow: hidden;
        opacity: 0;
        pointer-events: none;
        transition: opacity 0.25s ease 0.15s;
        min-width: 0;
    }
    .section.expanded .content {
        opacity: 1;
        pointer-events: auto;
    }
</style>

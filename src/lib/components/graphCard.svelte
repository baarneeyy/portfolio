<script lang="ts">
    import { createGitgraph, Orientation, templateExtend, TemplateName } from "@gitgraph/js";
    import { onMount } from "svelte";

    let gitgraph: ReturnType<typeof createGitgraph> | null = null;

    onMount(() => {
        const graphContainer = document.getElementById("edu-graph") as HTMLElement;

        gitgraph = createGitgraph(graphContainer, {
            // earliest at the top, newest at the bottom
            orientation: Orientation.VerticalReverse,
            author: "Me <tomas.vsetecka@tuta.com>",
            // (education blue, work green, projects purple)
            template: templateExtend(TemplateName.Metro, {
                colors: ["#3b82f6", "#22c55e", "#a855f7"],
                commit: {
                    message: {
                        displayAuthor: false,
                        displayHash: false,
                    },
                },
            }),
        });

        // -- Education timeline (master)
        const education = gitgraph.branch("education");

        education.commit({
            subject: "College start - Sep 2023",
            body: "Enrolled at FIMU for CompSci bachelors.",
        });

        // Left college Jan 2024 to join Binary Confidence (education on hold)
        education.commit({
            subject: "End of 1st College attempt - Jan 2024",
            body: "Switch CompSci studies for Work.",
            tag: "Left college",
        });

        // -- Work timeline (branches off the leave commit)
        const work = gitgraph.branch("work");

        work.commit({
            subject: "Career start - Jan 2024",
            body: "QA engineer / Tester for a web-app.",
            tag: "Binary Confidence",
        });

        work.commit({
            subject: "Manual + Automated testing - 2024",
            body: "Bug reports, regression runs, test cases.",
        });

        work.commit({
            subject: "Expanded test coverage - 2025",
            body: "New test suites, CI checks.",
        });

        // -- Education resumes (Sep 2025) while still working
        education.commit({
            subject: "Returned to college - Cybersecurity - Sep 2025",
            body: "Started anew with Cybersecurity at FIMU.",
        });

        education.commit({
            subject: "Cybersecurity coursework, 2025-2026",
            body: "Ongoing studies alongside work.",
        });

        // End of Work
        work.commit({
            subject: "Final stretch at Binary Confidence - early 2026",
            body: "Wrapping up projects.",
            tag: "Left · Mar 2026",
        });

        // Merge work back into education
        education.merge(work, "Closed work chapter - full focus on studies");

        // -- Projects (2026)
        const projects = gitgraph.branch("projects");

        projects.commit({
            subject: "Built portfolio site - 2026",
            body: "SvelteKit + DaisyUI.",
            tag: "Portfolio",
        });

        projects.commit({
            subject: "Project Grower - 2026",
            body: "Small 2D game demo written in Lua.",
        });

        projects.commit({
            subject: "bGone - 2026",
            body: "file cleanup utility in Python.",
        });

        // Merge projects into education to finish the timeline
        education.merge(projects, "NOW - 2026");
    });
</script>

<div class="card bg-base-100 card-xl shadow-sm">
  <div class="card-body">
    <h2 class="card-title justify-center mb-12 mr-12">Education &amp Experience timeline</h2>
    <div id="edu-graph"></div>
    <div class="justify-end card-actions"></div>
  </div>
</div>

<style>
    /* Add vertical space between commit's subject line and its
       body description. gitgraph renders the body as <foreignObject><p>, and
       its height calc (rect.height + marginTop) accounts for margin-top, so
       the foreignObject grows to fit, no clip. */
    #edu-graph :global(foreignObject > p) {
        margin-top: 1em;
    }
</style>

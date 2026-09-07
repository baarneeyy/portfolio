<script lang="ts">
    import { createGitgraph } from "@gitgraph/js";
    import { onMount } from "svelte";

    let gitgraph = null;

    onMount(() => {
        const graphContainer = document.getElementById("edu-graph") as HTMLElement;
        gitgraph = createGitgraph(graphContainer);

        const master = gitgraph.branch("master");
        master.commit("Init the project");
        master
            .commit("Add README")
            .commit("Add tests")
            .commit("Implement feature");
        master.tag("v1.0");
        const newFeature = gitgraph.branch("new-feature");
        newFeature.commit("Implement an awesome feature");
        master.commit("Hotfix a bug");
        newFeature.commit("Fix tests");
        // Merge `newFeature` into `master`
        master.merge(newFeature, "Release new version");
    });

</script>

<div class="card w-96 bg-base-100 card-xl shadow-sm">
  <div class="card-body">
    <h2 class="card-title">Xlarge Card</h2>
    <p>A card component has a figure, a body part, and inside body there are title and actions parts</p>
    <div id="edu-graph"></div>
    <div class="justify-end card-actions"></div>
  </div>
</div>

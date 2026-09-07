<script>
  import CardGeneric from "$lib/components/cardGeneric.svelte"

  let selectedProject = $state(null);
  const projects = [
    { name : "bGone", description: "python script for deleting old and unused files" },
    { name : "untitled-demo", description: "barebones 2d game demo made with Love2D"},
  ]
</script>

<h1>Projects</h1>
<CardGeneric {...projects[0]} click={() => {selectedProject = projects[0];  my_modal_1.showModal()}}/>
<CardGeneric {...projects[1]} click={() => {selectedProject = projects[1];  my_modal_1.showModal()}}/> <!-- TODO: separate modal -->

<!-- Open the modal using ID.showModal() method -->
<dialog id="my_modal_1" class="modal">
  <div class="modal-box">
    {#if selectedProject}
      <h3 class="text-lg font-bold">{selectedProject.name}</h3>
      <p class="py-4">Press ESC key or click the button below to close</p>
    {/if}
    <div class="modal-action">
      <form method="dialog">
        <!-- if there is a button in form, it will close the modal -->
        <button class="btn">Close</button>
      </form>
    </div>
  </div>
</dialog>

<script>
    import InfoPanel from "./infoPanel.svelte";

</script>
<div class="card lg:card-side bg-base-100 shadow-sm">
  <figure>
    <img
      src="https://img.daisyui.com/images/stock/photo-1494232410401-ad00d5433cfa.webp"
      alt="Album" />
  </figure>
  <div class="card-body">
    <h2 class="card-title">A wild developer has appeared!</h2>
    <p>looking for jobs atm</p>
    <div class="card-actions justify-end">
      <InfoPanel />

      <!--- trying using info panel for btn-->
      <button type="button" class="alert alert p-10px" tabindex="0" onclick={() => {console.log('lol');}}>
        click
      </button>
      <button class="btn btn-primary">add</button>
    </div>
  </div>
</div>

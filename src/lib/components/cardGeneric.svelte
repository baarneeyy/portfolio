<script>
  let props = $props();
</script>

<div class="card w-96 bg-base-100 card-xl shadow-sm">
  <div class="card-body">
    <h2 class="card-title">{props.name}</h2>
    <p>{props.description}</p>
    <div class="justify-end card-actions">
      <button class="btn btn-primary" onclick={props.click}>See more</button>
      <button class="btn btn-primary">Repo Link</button>
    </div>
  </div>
</div>

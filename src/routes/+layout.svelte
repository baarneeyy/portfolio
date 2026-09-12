<script lang="ts">
	import '/src/app.css';
	import favicon from '$lib/assets/favicon.svg';

	let { children } = $props();
</script>

<svelte:head><link rel="icon" href={favicon} /></svelte:head>
<div class="content-wrap">
{@render children()}
</div>
<footer class="footer sm:footer-horizontal footer-center bg-base-300 text-base-content p-4">
  <aside>
    <p>{new Date().getFullYear()} - Designed by me :]</p>
  </aside>
</footer>

<style>
    .footer {
        position: fixed;
        left: 0;
        bottom: 0;
    }
</style>

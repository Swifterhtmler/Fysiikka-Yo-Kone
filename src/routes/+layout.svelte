<script>
	import './layout.css';
	
	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href="/logos.png" type="image/png" />
</svelte:head>

{@render children()}

<script lang="ts">
	import type { NodeViewProps } from '@tiptap/core';
	import MediaExtended from './MediaExtended.svelte';

	const { ...rest }: NodeViewProps = $props();

	let mediaRef = $state<HTMLElement>();
</script>

<MediaExtended bind:mediaRef {...rest}>
	{@const node = rest.node}
	<img
		bind:this={mediaRef}
		src={node.attrs.src}
		alt={node.attrs.alt}
		title={node.attrs.title}
		style="max-width:var(--edra-image-max-width,300px); max-height:var(--edra-image-max-height,200px); width:auto; height:auto; display:block;"
	/>
</MediaExtended>

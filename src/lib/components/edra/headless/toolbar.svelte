<script lang="ts">
	import commands from '../commands/toolbar-commands.js';
	import type { EdraToolbarProps } from '../types.js';
	import type { EdraToolBarCommands } from '../commands/types.js';
	import FontSize from './components/toolbar/FontSize.svelte';
	import QuickColors from './components/toolbar/QuickColors.svelte';
	import SearchAndReplace from './components/toolbar/SearchAndReplace.svelte';
	import ToolBarIcon from './components/ToolBarIcon.svelte';

	const { editor, class: className, excludedCommands, children }: EdraToolbarProps = $props();

	// Normalize exclusions: allow users to pass either group keys or command names,
	// and also accept common aliases for commands and special components.
	const aliasMap: Record<string, string[]> = {
		// friendly -> actual keys/names
		heading1: ['h1'],
		heading2: ['h2'],
		heading3: ['h3'],
		heading4: ['h4'],
		codeBlock: ['code'],
		undo: ['undo'],
		redo: ['redo'],
		video: ['video-placeholder', 'video'],
		table: ['table'],
		fontSize: ['fontSize'],
		quickColor: ['quickColor'],
		searchAndReplace: ['searchAndReplace']
	};

	// Build a Set of excluded tokens expanded via aliases
	const excludedSet = new Set<string>();
	if (excludedCommands) {
		for (const token of excludedCommands) {
			excludedSet.add(token);
			const mapped = aliasMap[token];
			if (mapped) mapped.forEach((m) => excludedSet.add(m));
		}
	}

	// Determine whether to render special components
	const showFontSize = !excludedSet.has('fontSize');
	const showQuickColors = !excludedSet.has('quickColor');
	const showSearchAndReplace = !excludedSet.has('searchAndReplace');

	const filteredCommands = (Object.entries(commands) as [string, EdraToolBarCommands[]][])
		.map(([key, cmdArray]) => [
			key,
			cmdArray.filter((c) => !excludedSet.has(c.name)) as EdraToolBarCommands[]
		] as [string, EdraToolBarCommands[]])
		.filter(([key, cmdArray]) => !excludedSet.has(key) && cmdArray.length > 0);

	let show = $state<boolean>(false);
</script>

	<div class={`edra-toolbar ${className}`}>
		{#if children}
			{@render children()}
		{:else}
			{#if !show}
				{#each filteredCommands as group (group[0])}
					{@const commandGroup = group[1]}
					{#each commandGroup as command (command)}
						<ToolBarIcon {editor} {command} />
					{/each}
				{/each}
				{#if showFontSize}
					<FontSize {editor} />
				{/if}
				{#if showQuickColors}
					<QuickColors {editor} />
				{/if}
			{/if}
			{#if showSearchAndReplace}
				<SearchAndReplace {editor} bind:show />
			{/if}
		{/if}
	</div>

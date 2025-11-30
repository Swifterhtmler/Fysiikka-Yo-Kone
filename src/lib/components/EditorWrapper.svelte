<script lang="ts">
	import { browser } from '$app/environment';
	import type { Content, Editor } from '@tiptap/core';
	import { EdraEditor, EdraToolBar, EdraBubbleMenu } from './edra/headless/index.js';
	import defaultContent from './edra/default_content.js';
	import DragHandle from './edra/components/DragHandle.svelte';

	interface Props {
		width?: number;

		height?: number;

		excludedCommands?: string[];

		/** Unique ID for this editor instance (ensures isolated localStorage keys) */
		editorId?: string;

		localKey?: string;

		/** maximum image width in px (preferred name) */
		imageMaxWidth?: number;

		/** maximum image height in px (preferred name) */
		imageMaxHeight?: number;

		// legacy / user-requested misspelled prop names (accepted and mapped)
		imagexasizewidth?: number;

		imagemaxsizeheight?: number;
	}

	const defaultExcluded = ['video', 'code', 'video-placeholder', 'codeBlock'];

	let {
		width,
		height,
		excludedCommands = defaultExcluded,
		editorId,
		localKey = 'edra-content',
		imageMaxWidth,
		imageMaxHeight,
		imagexasizewidth,
		imagemaxsizeheight
	}: Props = $props();

	const excluded = excludedCommands;

	const computedWidth = width ? `${width}px` : '100%';
	const computedHeight = height ? `${height}px` : '100%';

	const finalImageMaxWidth = imageMaxWidth ?? imagexasizewidth ?? 300;
	const finalImageMaxHeight = imageMaxHeight ?? imagemaxsizeheight ?? 200;

	// Use editorId + localKey for unique storage per instance, or just localKey if editorId not provided
	const storageKey = editorId ? `${editorId}:${localKey}` : localKey;

	// Editor states
	let content = $state<Content>();
	let editor = $state<Editor>();

	$effect(() => {
		if (content) {
			$inspect('[DEBUG] Content', content);
			try {
				localStorage.setItem(storageKey, JSON.stringify(content));
			} catch (e) {
				// ignore storage errors (e.g., quota, private mode)
			}
		}
	});

	if (browser) {
		try {
			const rawDataString = localStorage.getItem(storageKey);

			if (rawDataString === null) {
				content = defaultContent;
			} else {
				const rawData: Content = JSON.parse(rawDataString);
				content = rawData;
			}
		} catch (e) {
			content = defaultContent;
		}
	}

	function onUpdate() {
		content = editor?.getJSON();
	}

	// Expose convenience functions so parent components (via `bind:this`) or
	// tests can explicitly save/load/clear content from localStorage.
	export function saveToLocal() {
		try {
         console.log("Injecting old content")
			localStorage.setItem(storageKey, JSON.stringify(content));
		} catch (e) {
			// ignore
		}
	}

	export function loadFromLocal(): boolean {
		try {
			const raw = localStorage.getItem(storageKey);
			if (!raw) return false;
			content = JSON.parse(raw);
			return true;
		} catch (e) {
			return false;
		}
	}

	export function clearLocal() {
		try {
			localStorage.removeItem(storageKey);
		} catch (e) {
			// ignore
		}
	}

	export function getContent() {
		return content;
	}

	/**
	 * Sync content from localStorage to Supabase.
	 * @param supabaseClient - imported supabase client
	 * @param table - table name (e.g., 'documents')
	 * @param userId - user ID for filtering/storing
	 * @param docId - document ID (optional; generates UUID if not provided)
	 * @returns Promise with success status and message
	 */
	export async function syncToSupabase(
		supabaseClient: any,
		table: string,
		userId: string,
		docId?: string
	): Promise<{ success: boolean; message: string; id?: string }> {
		try {
			// Get current content from localStorage
			const raw = localStorage.getItem(storageKey);
			if (!raw) {
				return { success: false, message: 'No content in localStorage' };
			}

			const contentData = JSON.parse(raw);
			const id = docId || crypto.randomUUID();

			// Insert or update in Supabase
			const { error } = await supabaseClient
				.from(table)
				.upsert(
					{
						id,
						user_id: userId,
						content: contentData,
						updated_at: new Date().toISOString()
					},
					{ onConflict: 'id' }
				)
				.select();

			if (error) {
				return { success: false, message: `Supabase error: ${error.message}` };
			}

			return { success: true, message: 'Synced to Supabase', id };
		} catch (err) {
			return { success: false, message: `Sync error: ${err instanceof Error ? err.message : String(err)}` };
		}
	}

   
</script>

<div style="display:flex; align-items:center; justify-content:center; width:100%; height:100%;">

	<div style={`width: ${computedWidth}; height: ${computedHeight}; max-width:100%; max-height:100%; display:flex; flex-direction:column; --edra-image-max-width: ${finalImageMaxWidth}px; --edra-image-max-height: ${finalImageMaxHeight}px;`}>
		{#if editor}
			<div style="border: 1px solid #ccc; border-bottom: none; border-radius: 4px 4px 0 0; padding: 4px; gap: 5px;">
				<EdraToolBar {editor} excludedCommands={excluded} />
			</div>
			<EdraBubbleMenu {editor} />
		<!--	<DragHandle {editor} /> -->
		{/if}
		<div style="border: 1px solid #ccc; border-radius: 0 0 4px 4px; overflow: hidden; flex:1; min-height:150px;">
			<div style="width:100%; height:100%;">
				<EdraEditor
					bind:editor
					{content}
					{onUpdate}
				/>
			</div>
		</div>
	</div>
</div>

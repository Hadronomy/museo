<script lang="ts">
	import { onMount } from 'svelte';

	import 'reveal.js/dist/reveal.css';
	import 'reveal.js/dist/theme/black.css';
	import 'reveal.js/plugin/highlight/monokai.css';

	import Presentation from './presentation.svelte';

	onMount(async () => {
    const Reveal = await (await import("reveal.js")).default;
    const Markdown = await (await import("reveal.js/plugin/markdown/markdown.esm")).default;
    const Highlight = await (await import("reveal.js/plugin/highlight/highlight.esm")).default;
    const Notes = await (await import("reveal.js/plugin/notes/notes.esm")).default;

		const deck = new Reveal({
			plugins: [Markdown, Highlight, Notes],
			autoAnimateEasing: 'ease',
			autoAnimateDuration: 1,
			hash: true
			// controls: false,
			// progress: false
		});

		deck.initialize();
	});
</script>

<div class="reveal">
	<div class="slides">
		<Presentation />
	</div>
</div>

<script>
	import Card from '$components/Card.svelte';
	import CodeMirror from 'svelte-codemirror-editor';
	import { html } from '@codemirror/lang-html';

	const kind = 'neutral';
</script>

<Card
	{kind}
	header={{
		text: 'Usage of content-based color palettes',
		id: 'radio-active-usage',
		alt: 'Usage of Content-based color palettes'
	}}
>
	<div class="active-usage">
		<CodeMirror
			readonly={true}
			tabSize={2}
			useTab={false}
			basic={true}
			value={`<script>\n import { RadioActive } from 'radio-color-system';\n</script>\n\n<RadioActive>\n	<img src="./image.png" alt="Rick Astley dancing" />\n	<div class="card dynamic-90 dynamic-90-text">\n		<h3>Dynamic Color</h3>\n		<p>Dynamic colors are great</p>\n	</div>\n</RadioActive>\n\n<style>\n.card {\n	padding: 1rem;\n	border-radius: 0.5rem;\n	margin-bottom: 1rem;\n} \n</style>`.replace(
				' *{}',
				''
			)}
			lang={html()}
		/>

		<a href="#radio-active" class="{kind}-font-90 mdc-typography--subtitle2 underline"
			>Advanced usage</a
		>
	</div>
</Card>

<style lang="scss">
	.active-usage {
		margin-top: 2rem;
	}

	.active-usage :global(.cm-editor) {
		background: var(--neutral-90);
		color: var(--neutral-font-90);
		height: 580px;
	}

	h5 {
		margin: 1rem 0 0 0;
	}

	a {
		padding: 0 1rem;
	}
	// TODO: Remove editor styles from here
	:global(.ͼ1 .cm-scroller) {
		font-family: 'Fira Code', monospace;
	}

	:global(.ͼ4 .cm-line) {
		caret-color: transparent !important;
		padding: 0.25rem 0 0.25rem 0.5rem;
	}

	:global(.cm-editor) {
		-moz-osx-font-smoothing: grayscale;
		-webkit-font-smoothing: antialiased;
		font-size: 0.875rem;
		line-height: 1.25rem;
		font-weight: 400;
		letter-spacing: 0.0178571429em;
		text-decoration: inherit;
		text-transform: inherit;

		height: 660px;
		border-radius: 8px;
		padding: 1rem;

		:global([title='Fold line']) {
			opacity: 0;
		}
	}

	:global(.ͼ2 .cm-activeLine) {
		background-color: var(--primary-90);
		border-top-right-radius: 4px;
		border-bottom-right-radius: 4px;
	}

	:global(.ͼ2 .cm-gutters) {
		background: var(--neutral-90);
		border-right: 2px solid var(--primary-90);
	}

	:global(.ͼ2 .cm-activeLineGutter) {
		background-color: var(--primary-80);
		color: var(--primary-font-80);
	}

	:global(.ͼg, .ͼl, .ͼi) {
		color: var(--primary-font-90);
	}

	:global(.ͼd) {
		color: var(--secondary-50);
	}

	:global(.ͼb, .ͼe) {
		color: var(--tertiary-30);
	}

	:global(.ͼ1 .cm-lineNumbers .cm-gutterElement) {
		display: flex;
		align-items: center;
	}

	:global(.cm-gutter.cm-lineNumbers .cm-gutterElement.cm-activeLineGutter) {
		border-top-left-radius: 4px;
		border-bottom-left-radius: 4px;
	}

	:global(.ͼ2 .cm-gutters) {
		color: var(--neutral-font-90);
	}
</style>

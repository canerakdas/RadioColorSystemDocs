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
		alt: 'Usage of Content-based color palettes',
		type: 'h2'
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
</style>

<script>
	import Card from '$components/Card.svelte';
	import CodeMirror from 'svelte-codemirror-editor';
	import { html } from '@codemirror/lang-html';

	const kind = 'neutral';
</script>

<Card {kind} header={{ text: 'Basic Usage', id: 'usage', alt: 'Basic Usage of RadioStatic' }}>
	<div class="usage">
		<CodeMirror
			readonly={true}
			tabSize={2}
			useTab={false}
			basic={true}
			value={`<script>
  import { RadioStatic } from 'radio-color-system';

  let colors = [{
      color: '#0652da',
      name: ['primary', 'secondary', 'tertiary']
    },
    {
      color: '#919191',
      name: 'neutral'
    }
  ];
</script>

<RadioStatic {colors} async={true} />

<div class="primary-90 primary-90-text">
  Primary Color
</div>

<div class="secondary-50 primary-50-text">
  Secondary Color
</div>

<div class="tertiary-40 tertiary-40-text">
  Tertiary Color
</div>`.replace(' *{}', '')}
			lang={html()}
		/>
		<div>
			<h3 class="mdc-typography--headline5">Motivation</h3>
			<p class="mdc-typography--body2">
				System design libraries offer a plethora of elements that can be overwhelming to navigate.
				However, incorporating a system change library into your project can enhance your
				productivity and simplify development processes. Yet, customization and optimization can be
				challenging to implement. Fortunately, Svelte's unique and intuitive structure eliminates
				the need for most component library dependencies.
			</p>
			<p class="mdc-typography--body2">
				With Radio Color System & Svelte, you can easily create your own color system and rapidly
				develop your desired components.
			</p>
			<a href="#radio-static" class="{kind}-font-90 mdc-typography--subtitle2 underline"
				>Advanced usage</a
			>
		</div>
	</div>
</Card>

<style lang="scss">
	.usage {
		display: flex;
		gap: 2rem;
		margin-top: 2rem;

		@media (max-width: 1024px) {
			flex-direction: column;
			gap: 1rem;
		}
	}

	.usage :global(.cm-editor) {
		background: var(--neutral-90);
		color: var(--neutral-font-90);
	}

	h5,
	h4,
	h3,
	h2 {
		margin: 1rem 0 0 0;
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

		@media (max-width: 1024px) {
			padding: 1rem 0;
		}

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

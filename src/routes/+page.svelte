<script>
	import Header from './Header.svelte';
	import Card from '../components/Card.svelte';
	import RadioInput from '../components/RadioInput.svelte';
	import Subtitle from '../components/Subtitle.svelte';
	import Attribute from '../components/Attribute.svelte';
	import styles from './styles.scss';
</script>

<div class="container">
	<Header />
	<div class="attr">
		<div class="neutral-80 test">
			<div class="at neutral-font-80">
				<span class="material-symbols-outlined"> format_paint </span>
				<span class="mdc-typography--subtitle2">Colors</span>
			</div>
			<fieldset>
				<RadioInput id="huey" name="a" value="huey" checked label="Primary Color" />
				<RadioInput id="dewey" name="a" value="dewey" label="Secondary Color" />
				<RadioInput id="c" name="a" value="c" label="Tertiary Color" />
				<RadioInput id="d" name="a" value="d" label="Neutral" />
			</fieldset>
		</div>
		<div class="primary-0 test">
			<div class="at primary-font-0">
				<span class="material-symbols-outlined"> palette </span>
				<span class="mdc-typography--subtitle2">Palette</span>
			</div>
			<div class="hece">
				{#each [0, 10, 20, 30, 40, 50, 60, 70, 80, 90, 100] as codes}
					<div class={`primary-${codes} primary-font-${codes} hehe mdc-typography--subtitle2`}>
						{codes}
					</div>
				{/each}
			</div>
		</div>
	</div>
	<Card header="Motivation" kind="secondary">
		<p>
			System design libraries offer a plethora of elements that can be overwhelming to navigate.
			However, incorporating a system change library into your project can enhance your productivity
			and simplify development processes. Yet, customization and optimization can be challenging to
			implement. Fortunately, Svelte's unique and intuitive structure eliminates the need for most
			component library dependencies.
		</p>
		<p>
			With Radio Color System & Svelte, you can easily create your own color system and rapidly
			develop your desired components.
		</p>
	</Card>

	<Card header="RadioStatic" kind="neutral" id="radio-static" alt="Radio Static Component">
		<Attribute
			name="async"
			type="boolean"
			defaultValue="false"
			description="When true, the component will be rendered asynchronously. This is useful for optimizing performance when the component is rendered in a loop. Also be careful when using this, cause of async color load user can see a flash of unstyled content."
			element="radio-static"
			optional
		/>
		<Attribute
			name="colors"
			type="ColorOption[]"
			defaultValue="[]"
			description="The options for generating color variants"
			href="radio-static-color-option"
			alt="Color Option Attribute"
		/>
		<Attribute name="target" defaultValue=":root" type="string" element="radio-static" optional />
	</Card>
	<Card header="RadioActive" kind="primary" id="radio-active" alt="Radio Active Component">
		<Attribute
			name="async"
			type="boolean"
			defaultValue="false"
			description="By default this value is false, when the image loaded after than generates the color. If you want to dont use default color set this value to true."
			element="radio-active"
			kind="primary"
			optional
		/>
		<Attribute
			name="target"
			type="string"
			defaultValue="dynamic"
			description="It adds an id attribute to the element it is used in and creates the styles to be created under this id. In cases where it is used in more than one place on the page, it is necessary to give a unique value."
			element="radio-active"
			kind="primary"
			optional
		/>
		<Attribute
			name="color"
			type="ColorOption"
			description="It adds an id attribute to the element it is used in and creates the styles to be created under this id. In cases where it is used in more than one place on the page, it is necessary to give a unique value."
			href="#radio-static-color-option"
			alt="Color Option Attribute"
			kind="primary"
			optional
		>
			<span class="mdc-typography--subtitle1">Default</span>
			<pre><code
					>&lbrace;
  color: &lbrace;h: 0, s: 0, l: 50&rbrace;,
  name: 'dynamic',
&rbrace;</code
				></pre>
		</Attribute>
	</Card>
	<Card
		kind="neutral"
		header="ColorOption"
		id="radio-static-color-option"
		alt="Color Option Attribute"
	>
		<Attribute
			name="color"
			type="Color"
			href="#radio-static-color"
			alt="Color Attribute"
			description="The base color to use for generating the color variants."
		/>
		<Attribute
			name="prefix"
			type="string"
			description="A prefix to use when generating token names."
			element="color-option-prefix"
			optional
		/>
		<Attribute
			name="name"
			type="string"
			description="A name to use when generating token names."
			element="color-option-name"
			optional
		/>
		<Attribute
			name="suffix"
			type="string"
			description="A suffix to use when generating token names."
			element="color-option-suffix"
			optional
		/>
		<Attribute
			name="dark"
			type="boolean"
			description="Whether to generate dark color variants."
			element="color-option-dark"
			optional
		/>
		<Attribute
			name="font"
			type="boolean"
			description="Whether to generate font color variants."
			element="color-option-font"
			optional
		/>
		<Attribute
			name="selector"
			type="object"
			description="An object specifying which selectors to generate."
			element="color-option-selector"
			optional
		>
			<Attribute
				name="attribute"
				type="boolean"
				description="Whether to generate attribute selectors."
				element="color-option-selector-attribute"
				optional
				sub
			/>
			<Attribute
				name="class"
				type="boolean"
				description="Whether to generate class selectors."
				element="color-option-selector-class"
				optional
				sub
			/>
		</Attribute>
		<Attribute
			name="theme"
			type="object"
			description="An object specifying color variants to use when generating token styles."
			element="color-option-theme"
			optional
		>
			<Attribute
				name="darken"
				type="ColorVariant"
				description="A function that returns an array of objects representing dark color variants."
				href="#color-variant-ColorVariant()"
				optional
				sub
			/>
			<Attribute
				name="lighten"
				type="ColorVariant"
				description="A function that returns an array of objects representing light color variants."
				href="#color-variant-ColorVariant()"
				optional
				sub
			/>
		</Attribute>
	</Card>
	<Card
		kind="primary"
		header="ColorVariant"
		id="radio-static-color-variant"
		alt="Color Variant Attribute"
	>
		<Attribute
			name="ColorVariant()"
			type="function"
			description="A function that returns an array of objects representing the color variant. The returned objects should have the `count`, `background`, and `foreground` properties."
			element="color-variant"
			kind="primary"
		/>
		<Attribute
			name="color"
			type="Color"
			href="#radio-static-color"
			alt="Color Attribute"
			description="The color to use for the variant."
			element="color-variant"
			kind="primary"
		/>
	</Card>
	<Card kind="neutral" header="Color" id="radio-static-color" alt="Color Attribute">
		<Attribute
			name="h"
			type="number"
			description="The hue value of the color (0-360)"
			element="hue"
		/>
		<Attribute
			name="s"
			type="number"
			description="The saturation value of the color (0-100)"
			element="hue"
		/>
		<Attribute
			name="l"
			type="number"
			description="The lightness value of the color (0-100)"
			element="hue"
		/>
	</Card>
	<Card header="Example usage of dynamic colors">haha</Card>
</div>

<div class="neutral-80 neutral-font-80">i have spoken</div>

<style lang="scss">
	.attr {
		display: flex;
		background: var(--neutral-80);
		border-radius: 8px;
		flex-direction: column;
		overflow: hidden;
	}
	.at {
		display: flex;
		align-items: center;
		gap: 0.5rem;
		padding-left: 1rem;
		font-size: 0.75rem;
	}
	.test {
		margin: 0;
		display: flex;
		overflow: hidden;
		justify-content: space-between;
		align-items: center;
	}

	.hehe {
		width: 5rem;
		height: 5rem;
		display: flex;
		align-items: flex-start;
		justify-content: flex-end;
		padding: 0.5rem;
	}

	.hece {
		display: flex;
	}

	fieldset {
		display: flex;
		gap: 1rem;
		border: none;
		padding: 0 1rem;
		margin: 0;
	}

	.container {
		margin: auto;
		padding: 0 1rem;

		@media (min-width: 1281px) {
			max-width: 1280px;
		}

		@media (min-width: 1024) {
			max-width: 1024px;
		}
	}

	thead {
	}

	table {
		border-collapse: separate;
		border-spacing: 0;
		width: 100%;
	}

	thead th {
		padding: 0.5rem;
		font-weight: 400;
		background: var(--primary-90);
		color: var(--primary-font-90);
		text-align: -webkit-auto;
		border-top: 1px solid var(--primary-80);
		border-bottom: 1px solid var(--primary-80);
		height: 2.5rem;

		&:first-child {
			border-top-left-radius: 4px;
			border-bottom-left-radius: 4px;
			border-left: 1px solid var(--primary-80);
		}

		&:last-child {
			border-top-right-radius: 4px;
			border-bottom-right-radius: 4px;
			border-right: 1px solid var(--primary-80);
		}
	}

	tbody {
		margin: 0;
		padding: 0;
	}

	tbody tr {
		margin: 0;
		height: 3.33rem;

		&:last-child td {
			border-bottom: none;
		}
	}

	tbody tr td {
		border-bottom: 1px solid var(--primary-80);
		padding: 0.5rem;

		a {
			color: currentColor;
			font-weight: 500;

			&:hover {
			}
		}
	}

	h5 {
		a {
			color: currentColor;
			text-decoration: none;
		}
	}

	pre {
		border-radius: 8px;
		padding: 1rem;
		margin: 0;
		display: block;
		border: 1px solid var(--primary-80);
	}

	code {
		font-family: 'Fira Code', monospace;
		font-size: 14px;
	}

	.semibold {
		font-weight: 500;
		display: block;
		margin-bottom: 0.5rem;
		font-size: 0.75rem;
	}
</style>

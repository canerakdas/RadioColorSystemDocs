<script>
	import Card from '$components/Card.svelte';
	import Property from '$components/Property.svelte';

	const kind = 'primary';
</script>

<Card
	header={{
		text: 'RadioActive',
		id: 'radio-active',
		alt: 'Radio Active Component'
	}}
	{kind}
>
	<Property
		name="async"
		type="boolean"
		defaultValue="false"
		description="By default this value is false, when the image loaded after than generates the color. If you want to dont use default color set this value to true."
		element="radio-active"
		{kind}
		optional
	/>
	<Property
		name="target"
		type="string"
		defaultValue="dynamic"
		description="It adds an id attribute to the element it is used in and creates the styles to be created under this id. In cases where it is used in more than one place on the page, it is necessary to give a unique value."
		element="radio-active"
		{kind}
		optional
	/>
	<Property
		name="color"
		type="ColorOption"
		description="It adds an id attribute to the element it is used in and creates the styles to be created under this id. In cases where it is used in more than one place on the page, it is necessary to give a unique value."
		href="#radio-static-color-option"
		alt="Color Option Attribute"
		{kind}
		optional
	>
		<span class="mdc-typography--subtitle1">Default</span>
		<pre><code
				>&lbrace;
  color: &lbrace;h: 0, s: 0, l: 50&rbrace;,
  name: 'dynamic',
&rbrace;</code
			></pre>
	</Property>
</Card>

<style>
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
</style>

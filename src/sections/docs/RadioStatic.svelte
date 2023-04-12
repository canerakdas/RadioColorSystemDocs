<script>
	import Card from '$components/Card.svelte';
	import Property from '$components/Property.svelte';

	const kind = 'neutral';
</script>

<Card
	header={{
		alt: 'Radio Static Component',
		id: 'radio-static',
		text: 'RadioStatic'
	}}
	{kind}
>
	<Property
		name="async"
		type="boolean"
		defaultValue="false"
		description="When true, the component will be rendered asynchronously. This is useful for optimizing performance when the component is rendered in a loop. Also be careful when using this, cause of async color load user can see a flash of unstyled content."
		element="radio-static"
		optional
		{kind}
	/>
	<Property
		name="colors"
		type="ColorOption[]"
		defaultValue="[]"
		description="The options for generating color variants"
		href="radio-static-color-option"
		alt="Color Option Attribute"
		{kind}
	/>
	<Property
		name="target"
		defaultValue=":root"
		type="string"
		element="radio-static"
		optional
		{kind}
	/>
</Card>

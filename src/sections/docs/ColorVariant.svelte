<script>
	import Card from '$components/Card.svelte';
	import Property from '$components/Property.svelte';

	const kind = 'primary';
</script>

<Card
	{kind}
	header={{
		text: 'ColorVariant',
		id: 'color-variant-ColorVariant()',
		alt: 'Color Variant Attribute'
	}}
>
	<Property
		name="ColorVariant()"
		type="function"
		description="A function that returns an array of objects representing the color variant. The returned objects should have the `count`, `background`, and `foreground` properties."
		element="color-variant"
		{kind}
	/>
	<Property
		name="color"
		type="Color"
		href="#radio-static-color"
		alt="Color Attribute"
		description="The color to use for the variant."
		element="color-variant"
		{kind}
	/>
</Card>

<script>
	import Card from '$components/Card.svelte';
	import Property from '$components/Property.svelte';

	const kind = 'neutral';
</script>

<Card {kind} header={{ text: 'Color', id: 'radio-static-color', alt: 'Color Attribute' }}>
	<Property
		name="h"
		type="number"
		description="The hue value of the color (0-360)"
		element="hue"
		{kind}
	/>
	<Property
		name="s"
		type="number"
		description="The saturation value of the color (0-100)"
		element="hue"
		{kind}
	/>
	<Property
		name="l"
		type="number"
		description="The lightness value of the color (0-100)"
		element="hue"
		{kind}
	/>
</Card>

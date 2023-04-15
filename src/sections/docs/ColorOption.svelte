<script>
	import Card from '$components/Card.svelte';
	import Property from '$components/Property.svelte';

	const kind = 'neutral';
</script>

<Card
	{kind}
	header={{
		text: 'ColorOption',
		id: 'radio-static-color-option',
		alt: 'Color Option Attribute'
	}}
>
	<Property
		name="color | rgb | hex"
		type="ColorInput"
		description="The base color to use for generating the color variants. You can use Color type or a string in the format of rgb or hex."
		{kind}
	/>
	<Property
		name="prefix"
		type="string"
		description="A prefix to use when generating token names."
		element="color-option-prefix"
		optional
		{kind}
	/>
	<Property
		name="name"
		type="string"
		description="A name to use when generating token names."
		element="color-option-name"
		optional
		{kind}
	/>
	<Property
		name="suffix"
		type="string"
		description="A suffix to use when generating token names."
		element="color-option-suffix"
		optional
		{kind}
	/>
	<Property
		name="dark"
		type="boolean"
		description="Whether to generate dark color variants."
		element="color-option-dark"
		optional
		{kind}
	/>
	<Property
		name="font"
		type="boolean"
		description="Whether to generate font color variants."
		element="color-option-font"
		optional
		{kind}
	/>
	<Property
		name="selector"
		type="object"
		description="An object specifying which selectors to generate."
		element="color-option-selector"
		optional
		{kind}
	>
		<Property
			name="attribute"
			type="boolean"
			description="Whether to generate attribute selectors."
			element="color-option-selector-attribute"
			optional
			sub
			{kind}
		/>
		<Property
			name="class"
			type="boolean"
			description="Whether to generate class selectors."
			element="color-option-selector-class"
			optional
			sub
			{kind}
		/>
	</Property>
	<Property
		name="theme"
		type="object"
		description="An object specifying color variants to use when generating token styles."
		element="color-option-theme"
		optional
		{kind}
	>
		<Property
			name="darken"
			type="ColorVariant"
			description="A function that returns an array of objects representing dark color variants."
			href="#color-variant-ColorVariant()"
			optional
			sub
			{kind}
		/>
		<Property
			name="lighten"
			type="ColorVariant"
			description="A function that returns an array of objects representing light color variants."
			href="#color-variant-ColorVariant()"
			optional
			sub
			{kind}
		/>
	</Property>
</Card>

<script>
	import Container from '$components/Container.svelte';
	import { setContext } from 'svelte';
	import { writable } from 'svelte/store';
	import { RadioStatic } from 'radio-color-system';

	// Layouts
	import Header from '$layouts/Header.svelte';

	import '$utils/_variables.scss';

	let colors = writable([
		{
			color: { h: 220, s: 32, l: 48 },
			name: 'primary',
			selected: true
		},
		{ color: { h: 190, s: 20, l: 50 }, name: 'secondary' },
		{ color: { h: 30, s: 25, l: 61 }, name: 'tertiary' },
		{ color: { h: 270, s: 2, l: 57 }, name: 'neutral' }
	]);

	setContext('colors', colors);
</script>

<RadioStatic colors={$colors} async={true} />
<Container>
	<Header />
	<slot />
</Container>

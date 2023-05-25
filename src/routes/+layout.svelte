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
			color: { h: 5, s: 32, l: 48 },
			name: ['primary', 'secondary', 'tertiary'],
			selected: true
		},
		{ color: { h: 270, s: 2, l: 57 }, name: 'neutral' }
	]);

	setContext('colors', colors);

	import { dev } from '$app/environment';
	import { inject } from '@vercel/analytics';

	inject({ mode: dev ? 'development' : 'production' });
</script>

<RadioStatic colors={$colors} async={true} />
<Container>
	<Header />
</Container>

<slot />

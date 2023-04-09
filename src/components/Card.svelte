<script>
	import Header from './Header.svelte';
	export let kind = 'primary';
	export let header = '';
	export let headerType = 'h4';
	export let id = '';
	export let alt = '';

	const classes = {
		primary: 'primary-90 primary-font-90',
		neutral: 'neutral-90 neutral-font-90',
		secondary: 'secondary-90 secondary-font-90',
		tertiary: 'tertiary-90 tertiary-font-90'
	};
</script>

<div class={`card ${classes[kind]}`}>
	{#if header !== '' && headerType !== ''}
		<h3 {id} class="mdc-typography--headline4">
			{#if alt}
				<a href={`#${id}`} {alt}>{header}</a>
			{:else}
				{header}
			{/if}
		</h3>
	{/if}

	<div class={`card--content ${kind}-font-90`}>
		<slot />
	</div>
</div>

<style lang="scss">
	.card {
		display: flex;
		flex-direction: column;
		border-radius: 0.5rem;
		margin: 2rem 0;
	}

	.card--content :global(.attribute:last-child .seperator) {
		margin-bottom: 0;
		background-color: transparent;
	}
	h3 {
		padding: 0 1rem;
		margin-bottom: 0;

		a {
			color: currentColor;
			text-decoration: none;
		}
	}
</style>

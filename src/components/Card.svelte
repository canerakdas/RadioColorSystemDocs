<script>
	import Header from './Header.svelte';
	export let kind = 'primary';
	export let header = '';
	export let headerType = 'h4';
</script>

<div class={`card ${kind}-80 ${kind}-font-80`}>
	{#if header !== '' && headerType !== ''}
		<Header type={headerType}>{header}</Header>
	{/if}
	<div class={`card--content ${kind}-font-80`}>
		<slot />
	</div>
</div>

<style lang="scss">
	.card {
		border-radius: 0.5rem;
		padding: 1rem;
		margin: 2rem 0;
	}

	h3,
	h4,
	h5,
	h6 {
		margin: 0;
		padding: 0;
	}

	h3 {
		font-weight: 200;
		font-size: 48px;
		letter-spacing: 0;
	}

	h4 {
		font-weight: 200;
		font-size: 34px;
		letter-spacing: 0.25px;
	}

	h5 {
		font-weight: 400;
		font-size: 24px;
		letter-spacing: 0;
	}

	h6 {
		font-weight: 500;
		font-size: 20px;
		letter-spacing: 0.15px;
	}
</style>

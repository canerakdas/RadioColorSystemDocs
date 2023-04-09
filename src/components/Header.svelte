<script lang="ts">
	export let type = 'h4' as 'h1' | 'h2' | 'h3' | 'h4' | 'h5' | 'h6';
</script>

{#if type !== ''}
	<svelte:element this={type} {...$$restProps}><slot /></svelte:element>
{/if}

<style lang="scss">
	h1,
	h2,
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
		margin: 0.5rem 0 0 0;
	}

	h4 {
		font-weight: 200;
		font-size: 34px;
		letter-spacing: 0.25px;
		margin: 0.5rem 0 0 0;
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

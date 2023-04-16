<script>
	export let kind = 'primary';
	export let header = {
		text: '',
		id: '',
		alt: '',
		type: 'h4'
	};
</script>

<div class="card {kind}-90 {kind}-font-90">
	{#if header.text !== ''}
		<svelte:element this={header.type || 'h4'} id={header.id} class="mdc-typography--headline4">
			{#if header.alt}
				<a href="#{header.id}" alt={header.alt}>
					{header.text}
					<span class="material-symbols-outlined {kind}-80 {kind}-font-80"> link </span>
				</a>
			{:else}
				{header.text}
			{/if}
		</svelte:element>
	{/if}
	<div class="card--content {kind}-font-90">
		<slot />
	</div>
</div>

<style lang="scss">
	.card {
		display: flex;
		flex-direction: column;
		border-radius: 0.5rem;
		margin: 2rem 0;
		padding: 1rem;
	}

	h1,
	h2,
	h3,
	h4,
	h5 {
		margin: 1rem 0 0 0;

		&:hover {
			span {
				opacity: 1;
			}
		}

		a {
			display: flex;
			align-items: center;
			gap: 0.5rem;

			color: currentColor;
			text-decoration: none;

			span {
				padding: 0.5rem;
				border-radius: 0.5rem;
				opacity: 0;

				@media (prefers-reduced-motion: no-preference) {
					transition: all 0.2s ease-in-out;
				}
			}
		}
	}

	.card--content :global(.property:last-child hr) {
		margin-bottom: 0;
		background-color: transparent;
	}
</style>

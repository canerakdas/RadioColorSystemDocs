<script>
	export let kind = 'primary';
	export let header = {
		text: '',
		id: '',
		alt: ''
	};
</script>

<div class="card {kind}-90 {kind}-font-90">
	{#if header.text !== ''}
		<h4 id={header.id} class="mdc-typography--headline4">
			{#if header.alt}
				<a href="#{header.id}" alt={header.alt}>
					{header.text}
					<span class="material-symbols-outlined {kind}-80 {kind}-font-80"> link </span>
				</a>
			{:else}
				{header.text}
			{/if}
		</h4>
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

	h4 {
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
		}
	}

	h4 a span {
		padding: 0.5rem;
		border-radius: 0.5rem;
		opacity: 0;
		transition: all 0.2s ease-in-out;
	}

	.card--content :global(.property:last-child hr) {
		margin-bottom: 0;
		background-color: transparent;
	}
</style>

<script>
	export let kind = 'primary';
	export let icon = '';
	export let active = false;

	$: activeClass = active ? 'active' : '';
</script>

<button class="{activeClass} {kind}-70" {...$$restProps} on:click>
	<div class="button-inner {kind}-60 {kind}-font-70 mdc-typography--button">
		{#if icon !== ''}
			<span class="material-symbols-outlined {kind}-font-70"> {icon} </span>
		{/if}
		<slot />
	</div>
</button>

<style lang="scss">
	button {
		border: none;
		cursor: pointer;
		border-radius: 32px;
		display: flex;
		padding: 0;
		border: 4px solid transparent;

		.button-inner {
			display: flex;
			align-items: center;
			gap: 0.5rem;
			padding: 0.5rem 1rem;
			border-radius: 32px;

			span {
				font-size: 1.25rem;
			}
		}
	}
</style>

<script>
	export let kind = 'primary';
	export let code;
</script>

<div class="{kind}-{code} {kind}-font-{code} mdc-typography--subtitle2">
	{code}
</div>

<style>
	div {
		width: 4rem;
		min-width: 4rem;
		height: 4rem;
		display: flex;
		align-items: flex-start;
		justify-content: flex-end;
		padding: 0.5rem;

		@media (max-width: 768px) {
			min-width: calc(33.3333% - 1rem);
		}
	}
</style>

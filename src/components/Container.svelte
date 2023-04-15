<script>
	export let kind = 'neutral';
</script>

<div class={kind !== 'neutral' ? `${kind}-80 wide-content` : ''}>
	<div class="container"><slot /></div>
</div>

<style lang="scss">
	.container {
		margin: auto;
		padding: 0 1rem;

		@media (min-width: 1281px) {
			max-width: 1280px;
		}

		@media (min-width: 1024px) {
			max-width: 1024px;
		}
	}

	.wide-content {
		padding: 1px 0 2rem 0;

		.container {
			margin-top: 0;
		}
	}
</style>

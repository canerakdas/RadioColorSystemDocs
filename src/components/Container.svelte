<div class="container"><slot /></div>

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
</style>

<script>
	import Card from '$components/Card.svelte';
</script>

<div class="feature">
	<div class="dynamic-90 dynamic-font-90 feature--item">
		<span class="material-symbols-outlined"> point_scan </span>
		<p class="mdc-typography--body2">
			Works independently of any design system and it has a single purpose.
		</p>
	</div>
	<div class="dynamic-90 dynamic-font-90 feature--item">
		<span class="material-symbols-outlined"> deployed_code </span>
		<p class="mdc-typography--body2">
			Allows you to work asynchronously and gain from the colors that will come pre-loaded in your
			project.
		</p>
	</div>
</div>

<style lang="scss">
	.feature {
		display: flex;
		gap: 2rem;
		margin-top: 2rem;
		justify-content: space-evenly;
		flex-direction: row;
		flex-wrap: wrap;

		@media (max-width: 768px) {
			flex-direction: column;
		}
	}

	.feature--item {
		display: flex;
		flex-direction: row;
		align-items: flex-start;
		border-radius: 0.5rem;
		max-width: 48%;
		overflow: hidden;
		box-shadow: 0 0 0 1px var(--dynamic-90), 0 1px 3px 0 var(--dynamic-90);

		@media (max-width: 768px) {
			max-width: 100%;
		}
		p {
			padding: 1rem;
			margin: 0;
			width: 100%;

			display: flex;
		}

		span {
			font-size: 2rem;
			padding: 1rem;
			height: calc(100% - 2rem);
			display: flex;
			align-items: center;
		}
	}
</style>

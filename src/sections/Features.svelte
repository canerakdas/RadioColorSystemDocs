<script>
	import Card from '$components/Card.svelte';
</script>

<div class="feature">
	<div class="secondary-70 secondary-font-70 feature--item">
		<span class="material-symbols-outlined"> point_scan </span>
		<p class="mdc-typography--body2 secondary-80 secondary-font-80">
			Works independently of any design system and it has a single purpose.
		</p>
	</div>
	<div class="secondary-70 secondary-font-70 feature--item">
		<span class="material-symbols-outlined"> style </span>
		<p class="mdc-typography--body2 secondary-80 secondary-font-80">
			Can dynamically create a color palette based on visual content.
		</p>
	</div>
	<div class="secondary-70 secondary-font-70 feature--item">
		<span class="material-symbols-outlined"> deployed_code </span>
		<p class="mdc-typography--body2 secondary-80 secondary-font-80">
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

		@media (max-width: 768px) {
			flex-direction: column;
		}
	}

	.feature--item {
		display: flex;
		flex-direction: row;
		align-items: flex-start;
		border-radius: 0.5rem;
		max-width: 33.33333%;
		overflow: hidden;

		@media (max-width: 768px) {
			max-width: 100%;
		}
		p {
			padding: 1rem;
			margin: 0;
			width: 100%;
			height: 100%;

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

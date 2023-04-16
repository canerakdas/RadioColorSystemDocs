<script>
	import { RadioActive } from 'radio-color-system';

	import Features from '$sections/Features.svelte';

	import Card from '$components/Card.svelte';

	let index = 1;
	let images = [1, 2, 3];
	let target = `#image${index}`;
</script>

<RadioActive {target}>
	<Card kind="dynamic">
		<div class="dynamic--content">
			<div>
				<div class="dynamic--detail">
					<div class="active--container">
						<img
							width="256"
							height="256"
							id={`image${index}`}
							src={`./images/${index}.jpg`}
							alt="Selected image"
						/>
					</div>
					<div class="active--content">
						<h4 class="mdc-typography--headline4">
							{index === 2 ? 'This is the way' : 'Content-based color palettes'}
						</h4>
						<p class="mdc-typography--body2">
							RadioActive allows the end user to edit the theme according to the content they are
							interacting with. You can use it for content that may be irrelevant to your color
							palette and provide a more personalized experience.
						</p>
						<p class="mdc-typography--body2">
							It converts the color values in the current image to hsl format and groups them. Uses
							the dominant one of these colors, and expects the colors to be between a certain light
							and saturation value.
						</p>
						<p class="mdc-typography--body2">
							If the image is not suitable for the algorithm, it will return the default color. More
							information about the exceptions;
							<a
								href="https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/getImageData#exceptions"
								target="_blank"
								alt="MDN CanvasRenderingContext2D: getImageData() exceptions"
								class="underline dynamic-font-90"
								>CanvasRenderingContext2D: getImageData()
							</a>
						</p>
					</div>
				</div>
			</div>
		</div>
	</Card>
	<Card kind="dynamic">
		<div class="passive--container">
			{#each images.filter((image) => image !== index) as image}
				<img
					width="122"
					height="122"
					class={`${image === index ? 'active' : 'inactive'}`}
					id={`image${image}`}
					alt="Inactive image"
					src={`./images/${image}.jpg`}
					on:click={(event) => {
						target = `#image${image}`;
						index = image;
					}}
				/>
			{/each}
		</div>
	</Card>
	<Features />
</RadioActive>

<style lang="scss">
	.active--container {
		border-radius: 8px;
		overflow: hidden;
		display: flex;
		width: 256px;
		height: 256px;
		box-shadow: 0 0 0 1px currentColor, 0 1px 3px 0 currentColor;
	}
	.active--content {
		width: calc(100% - 256px);

		@media (max-width: 768px) {
			width: 100%;
		}
	}
	.inactive {
		width: 122px;
		cursor: pointer;
		border-radius: 8px;

		&:hover {
			transform: scale(1.2);
			transition: 0.3s ease all;
		}
	}

	.dynamic--detail {
		display: flex;
		flex-direction: row;
		gap: 2rem;
		align-items: center;

		@media (max-width: 768px) {
			flex-direction: column;
		}
	}
	.passive--container {
		display: flex;
		gap: 0.5rem;
	}

	:global(.underline) {
		text-decoration: underline;
	}

	h4 {
		margin: 1rem 0 0 0;
	}
</style>

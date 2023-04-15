<script>
	import { getContext, setContext } from 'svelte';

	import ColorBox from '$components/ColorBox.svelte';
	import Button from '$components/Button.svelte';

	let colors = getContext('colors');

	let color = $colors.find((color) => color.selected);
	$: kind = (color && color.name) || 'primary';

	let innerWidth = 0;
</script>

<svelte:window bind:innerWidth />

<div class="container">
	<div class="neutral-80 colors">
		<div class="title neutral-font-80">
			<span class="material-symbols-outlined"> format_paint </span>
			<span class="mdc-typography--subtitle2">Colors</span>
		</div>
		<div class="button-group">
			{#each $colors as color}
				<Button
					icon={color.selected ? 'radio_button_checked' : 'radio_button_unchecked'}
					kind={color.selected ? (kind === 'neutral' ? 'primary' : kind) : 'neutral'}
					active={color.selected}
					on:click={() => {
						kind = color.name;
						$colors.find((color) => color.selected).selected = false;
						color.selected = true;
					}}
				>
					{color.name}
				</Button>
			{/each}
		</div>
	</div>
	<div class={innerWidth <= 768 ? `${kind}-100 palette` : `${kind}-0 palette`}>
		<div class="title {kind}-font-0">
			<span class="material-symbols-outlined"> palette </span>
			<span class="mdc-typography--subtitle2">Palette</span>
		</div>
		<div class="palette--colors">
			{#each [0, 10, 20, 30, 40, 50, 60, 70, 80, 90, 100] as code}
				<ColorBox {kind} {code} />
			{/each}
		</div>
	</div>
</div>

<style lang="scss">
	.palette {
		display: flex;
		overflow: hidden;
		justify-content: space-between;
		align-items: center;
		gap: 1rem;

		@media (max-width: 768px) {
			flex-direction: column;
			gap: 0;
			align-items: flex-start;
		}
	}

	.palette--colors {
		display: flex;
		overflow: auto;
		@media (max-width: 768px) {
			flex-wrap: wrap;
		}
	}

	.colors {
		display: flex;
		overflow: hidden;
		justify-content: space-between;
		align-items: center;
		padding: 1rem 1rem 1rem 0;
		gap: 2rem;

		@media (max-width: 768px) {
			gap: 1rem;
			align-items: normal;
			flex-direction: column;
			padding: 0 0 1rem;
		}
	}

	.title {
		display: flex;
		align-items: center;
		gap: 0.5rem;
		padding-left: 1rem;

		@media (max-width: 768px) {
			padding: 1rem;
			font-size: 0.75rem;
			background: var(--neutral-70);
			color: var(--neutral-font-70);
			width: 100%;
		}
	}

	.button-group {
		display: flex;
		gap: 1rem;
		overflow: auto;

		@media (max-width: 768px) {
			padding-left: 1rem;
		}
	}

	.container {
		display: flex;
		background: var(--neutral-80);
		border-radius: 8px;
		flex-direction: column;
		overflow: hidden;
	}
</style>

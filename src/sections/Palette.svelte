<script>
	import { getContext, setContext } from 'svelte';

	import ColorBox from '$components/ColorBox.svelte';
	import Button from '$components/Button.svelte';

	let colors = getContext('colors');

	let color = $colors.find((color) => color.selected);
	$: kind = (color && color.name) || 'primary';

	let innerWidth = 0;
	let palette = false;
</script>

<svelte:window bind:innerWidth />

<div
	class="neutral-font-90 mdc-typography--subtitle1 accordion"
	on:click={() => (palette = !palette)}
>
	Show palette
	<span class="material-symbols-outlined"> expand_more </span>
</div>
<div class={palette === true ? 'container h-initial' : 'container'}>
	{#each $colors as color}
		{#if Array.isArray(color.name)}
			{#each color.name as name}
				<div
					class={innerWidth <= 768
						? `${name}-100 ${name}-font-100 palette`
						: `${name}-0 ${name}-font-100 palette`}
				>
					<div class="title {name}-font-0">
						<span class="material-symbols-outlined"> palette </span>
						<span class="mdc-typography--subtitle2">{name}</span>
					</div>
					<div class="palette--colors">
						{#each [0, 10, 20, 30, 40, 50, 60, 70, 80, 90, 100] as code}
							<ColorBox kind={name} {code} />
						{/each}
					</div>
				</div>
			{/each}
		{:else}
			<div class={innerWidth <= 768 ? `${color.name}-100 palette` : `${color.name}-0 palette`}>
				<div class="title {color.name}-font-0">
					<span class="material-symbols-outlined"> palette </span>
					<span class="mdc-typography--subtitle2">{color.name}</span>
				</div>
				<div class="palette--colors">
					{#each [0, 10, 20, 30, 40, 50, 60, 70, 80, 90, 100] as code}
						<ColorBox kind={color.name} {code} />
					{/each}
				</div>
			</div>
		{/if}
	{/each}
</div>

<style lang="scss">
	.palette {
		display: flex;
		overflow: hidden;
		justify-content: space-between;
		align-items: center;
		gap: 1rem;
		border-bottom: 1px solid currentColor;

		&:last-child {
			border-bottom: none;
		}

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

		span {
			width: 1.5rem;
			height: 1.5rem;
		}

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
		opacity: 0;
		height: 0;
	}

	.accordion {
		display: flex;
		align-items: center;
		cursor: pointer;
		padding: 1rem 0;
	}

	.h-initial {
		transition: 0.26s ease-in all;
		opacity: 1;
		height: initial;
	}
</style>

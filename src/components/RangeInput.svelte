<script>
	import Subtitle from './Subtitle.svelte';

	export let header = '';
	export let name = '';
	export let icon = '';
	export let min = 0;
	export let max = 100;
	export let value = 0;
	export let datalist = true;

	const getFrequencyClass = (frequency) => {
		if (frequency % 10 === 0) {
			return 'neutral-font-90 range-input--text';
		} else {
			return 'range-input--tickmark';
		}
	};

	const getFrequencyLabel = (frequency) => {
		if (frequency % 10 === 0) {
			return frequency;
		} else {
			return '';
		}
	};

	const id = `range-input-${name}`;
</script>

<div class="range-input">
	<Subtitle {icon}>{header}</Subtitle>
	<input class="range-input--input" type="range" list={id} {min} {max} bind:value />
	{#if datalist}
		<datalist class="range-input--datalist" {id}>
			{#each [0, 5, 10, 15, 20, 25, 30, 35, 40, 45, 50, 55, 60, 65, 70, 75, 80, 85, 90, 95, 100] as frequency}
				<option
					class={getFrequencyClass(frequency)}
					value={frequency}
					label={getFrequencyLabel(frequency)}
				/>
			{/each}
		</datalist>
	{/if}
</div>

<style lang="scss">
	.range-input {
		width: 400px;
	}

	.range-input--input {
		width: 100%;
		height: 0.625rem;

		-webkit-appearance: none;
		background: var(--neutral-80);

		border: 1px solid var(--neutral-font-80);
		border-radius: 2px;

		&::-webkit-slider-thumb {
			width: 2.5rem;
			height: 1.25rem;

			position: relative;
			top: -6px;
			z-index: 2;

			-webkit-appearance: none;
			background: var(--primary-50);
			box-shadow: inset 0 0 0 1px var(--neutral-font-50);
			border-radius: 1rem;
			cursor: pointer;

			transition: background 0.1s ease-in-out;

			&:hover {
				background: var(--primary-80);
				box-shadow: inset 0 0 0 2px var(--neutral-font-80);
			}
		}
	}

	.range-input--datalist {
		display: flex;
		justify-content: space-between;

		width: 100%;

		font-size: 0.75rem;
		font-weight: 200;

		padding-top: 0.15rem;
	}

	.range-input--text,
	.range-input--tickmark {
		position: relative;

		cursor: default;
		&::selection {
			background: transparent;
		}
	}

	.range-input--text:after,
	.range-input--tickmark:after {
		content: '';
		position: relative;
		width: 1px;
		height: 10px;
		overflow: hidden;
		display: inline-block;
		padding: 0;
		margin: 0;
		z-index: 1;
		background: var(--neutral-font-80);
		position: absolute;
		left: 50%;
		top: -17px;
	}
</style>

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
			return 'primary-font-80 range-input--text mdc-typography--caption';
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
	<div class="range-input--header primary-font-90">
		{#if icon !== ''}
			<span class="material-symbols-outlined">{icon}</span>
			<div class="mdc-typography--headline6">{header}</div>
		{/if}
	</div>
	<input class="range-input--input" type="range" list={id} {min} {max} bind:value />
	{#if datalist}
		<datalist class="range-input--datalist" {id}>
			{#each [0, 10, 20, 30, 40, 50, 60, 70, 80, 90, 100] as frequency}
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
		background: none;

		border: 1px solid var(--primary-font-80);
		border-radius: 2px;

		&::-webkit-slider-thumb {
			width: 2.5rem;
			height: 1.25rem;

			position: relative;
			top: -6px;
			z-index: 2;
			border-radius: 4px;

			-webkit-appearance: none;
			background: var(--primary-font-90);
			cursor: pointer;

			transition: background 0.1s ease-in-out;

			&:hover {
				background: var(--primary-font-80);
			}
		}
	}

	.range-input--datalist {
		display: flex;

		width: 100%;

		font-weight: 200;

		padding-top: 0.15rem;
	}

	.range-input--text,
	.range-input--tickmark {
		position: relative;
		width: 100%;
		text-align: center;
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
		background: var(--primary-font-80);
		position: absolute;
		left: 0;
		top: -17px;
	}

	.range-input--header {
		display: flex;
		gap: 0.5rem;
		align-items: center;
		margin-bottom: 0.5rem;
	}
</style>

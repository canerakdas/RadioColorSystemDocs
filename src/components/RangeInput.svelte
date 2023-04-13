<script>
	export let header = '';
	export let name = '';
	export let icon = '';
	export let min = 0;
	export let max = 100;
	export let value = 0;
	export let datalist = true;
	export let kind = 'primary';
	const getFrequencyClass = (frequency) => {
		return '';
	};

	const getFrequencyLabel = (frequency) => {
		if (frequency % 10 === 0) {
			return frequency;
		} else {
			return '';
		}
	};

	const id = `range-input-${name}`;
	const inputId = `input-${name}`;
</script>

<div class="range-input">
	<label for={inputId} class="range-input--header {kind}-font-90">
		{#if icon !== ''}
			<span class="material-symbols-outlined">{icon}</span>
			<div class="mdc-typography--headline6">{header}</div>
		{/if}
	</label>
	<input id={inputId} class="range-input--input" type="range" list={id} {min} {max} bind:value />
	{#if datalist}
		<div class="range-input--datalist" {id}>
			{#each [0, 10, 20, 30, 40, 50, 60, 70, 80, 90, 100] as frequency}
				<p class="{kind}-font-80 range-input--text mdc-typography--caption">
					{frequency}
				</p>
			{/each}
		</div>
	{/if}
</div>

<style lang="scss">
	.range-input {
		width: 100%;
		-webkit-appearance: none;
	}

	.range-input--input {
		-webkit-appearance: none;

		width: 100%;
		height: 0.625rem;

		background: none;

		border: 1px solid var(--primary-font-80);
		border-radius: 2px;

		/*Styling the track in Chrome*/
		&::-webkit-slider-runnable-track {
			-webkit-appearance: none;
		}

		&::-webkit-slider-thumb {
			-webkit-appearance: none;
			position: relative;

			width: 2.5rem;
			height: 1.25rem;

			z-index: 2;
			border-radius: 4px;

			-webkit-appearance: none;
			background: var(--primary-font-90);
			cursor: pointer;

			@media (prefers-reduced-motion: no-preference) {
				transition: background 0.1s ease-in-out;
			}
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

		position: relative;
		top: -12px;
		z-index: 1;
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

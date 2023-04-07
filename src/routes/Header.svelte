<script>
	import { onMount } from 'svelte';

	import { RadioStatic } from 'radio-color-system';
	const colors = [
		{ color: { h: 200, s: 12, l: 70 }, name: 'secondary' },
		{
			color: { h: 240, s: 48, l: 60 },
			name: 'primary'
		},
		{ color: { h: 342, s: 25, l: 61 }, name: 'tertiary' },
		{ color: { h: 270, s: 2, l: 57 }, name: 'neutral' }
	];
</script>

<RadioStatic {colors} async={true} />

<header>
	<div>
		<h1 class="header-logo">
			<span class="header-logo--main primary-font-70">Radio</span>
			<span class="header-logo--sub primary-font-70">Color System</span>
		</h1>
		<div class="color">
			{#each [50, 60, 70, 80, 90, 100] as codes}
				<div class={`primary-${codes} primary-font-${codes} color--item`} />
			{/each}
		</div>
	</div>
	<div class="vertical-container">
		<div class="vertical">
			<h2 class="neutral-font-80">Saturation</h2>
			<input
				class="sat"
				type="range"
				list="tickmark"
				min="0"
				max="100"
				bind:value={colors[1].color.s}
			/>

			<datalist id="tickmark">
				{#each [0, 5, 10, 15, 20, 25, 30, 35, 40, 45, 50, 55, 60, 65, 70, 75, 80, 85, 90, 95, 100] as frequency}
					<option
						class={frequency % 10 === 0
							? 'neutral-font-90 tickmark--text'
							: 'neutral-font-50 neutral-60 tickmark--tick'}
						value={frequency}
						label={frequency % 10 === 0 ? String(frequency) : ''}
					/>
				{/each}
			</datalist>
		</div>
		<div class="vertical">
			<h2 class="neutral-font-80">
				<span class="material-symbols-outlined"> light_mode </span>Lightning
				<span class="range--value primary-80 primary-font-80">{colors[1].color.l}%</span>
			</h2>
			<input
				class="sat"
				type="range"
				list="tickmark"
				min="0"
				max="100"
				bind:value={colors[1].color.l}
			/>

			<datalist id="tickmark">
				{#each [0, 5, 10, 15, 20, 25, 30, 35, 40, 45, 50, 55, 60, 65, 70, 75, 80, 85, 90, 95, 100] as frequency}
					<option
						class={frequency % 10 === 0 ? 'neutral-font-90 tickmark--text' : 'tickmark--tick'}
						value={frequency}
						label={frequency % 10 === 0 ? String(frequency) : ''}
					/>
				{/each}
			</datalist>
		</div>
	</div>
	<fieldset>
		<legend><span class="material-symbols-outlined">format_paint</span>Color scheme</legend>

		<div>
			<input type="radio" id="huey" name="drone" value="huey" checked />
			<label for="huey">Primary</label>
		</div>

		<div>
			<input type="radio" id="dewey" name="drone" value="dewey" />
			<label for="dewey">Secondary</label>
		</div>

		<div>
			<input type="radio" id="louie" name="drone" value="louie" />
			<label for="louie">Tertiary</label>
		</div>

		<div>
			<input type="radio" id="louie" name="drone" value="louie" />
			<label for="louie">Neutral</label>
		</div>
	</fieldset>
	<div class="knob">
		<div class="knob-container neutral-70">
			<div class="primary-60 knob-button">
				<div class="knob-button--inner neutral-70 neutral-font-70">360°</div>
			</div>
		</div>
	</div>
</header>

<style lang="scss">
	fieldset {
		border: 2px solid var(--neutral-80);
		color: var(--neutral-font-80);
		border-radius: 0.5rem;
		display: flex;
		flex-direction: column;
		gap: 0.5rem;
		min-width: 10rem;

		legend {
			color: var(--neutral-font-70);
			display: flex;
			align-items: center;
		}
	}
	input[type='radio'] {
		display: none;
	}

	label {
		display: flex;
		align-items: center;
		gap: 0.5rem;
		font-size: 12px;
		line-height: 16px;
		cursor: pointer;
		color: var(--neutral-font-80);
	}

	input[type='radio'] + label:before {
		content: '';
		display: inline-block;
		width: 1rem;
		height: 1rem;
		cursor: pointer;
		border-radius: 50%;
		background: var(--primary-font-50);
	}

	input[type='radio']:checked + label:before {
		content: '';
		width: 1rem;
		height: 1rem;
		border-radius: 50%;
		background: var(--primary-50);
		box-shadow: inset 0 0 0 2px var(--primary-font-50);
		transition: all 0.2s ease-in-out;
	}
	.color {
		position: absolute;
		display: flex;
		top: -80px;
		left: 0;
		transform: rotate(320deg);
		z-index: -1;

		&--item {
			width: 2em;
			height: 30rem;
		}
	}
	.knob-container {
		width: 7rem;
		height: 7rem;
		border-radius: 50%;
		display: flex;
		justify-content: center;
		align-items: center;
	}

	.knob-button {
		width: 6rem;
		height: 6rem;
		border-radius: 50%;
		display: flex;
		justify-content: center;
		align-items: center;

		&--inner {
			width: calc(6rem - 4px);
			height: calc(6rem - 4px);

			border-radius: 50%;
			display: flex;
			justify-content: center;
			align-items: center;
		}
	}

	input[type='range'] {
		-webkit-appearance: none;
		height: 10px;
		background: var(--neutral-80);
		border-radius: 2px;
		border: 1px solid var(--neutral-font-80);
	}

	input[type='range']::-webkit-slider-thumb {
		position: relative;
		top: -0.5rem;
		-webkit-appearance: none;
		height: 20px;
		width: 40px;
		border-radius: 1rem;
		background: var(--primary-50);
		cursor: pointer;
		box-shadow: inset 0 0 0 2px var(--primary-font-50);
		transition: background 0.1s ease-in-out;
		z-index: 2;
		&:hover {
			background: var(--primary-80);
			box-shadow: inset 0 0 0 3px var(--primary-font-80);
		}
	}

	header {
		position: relative;
		overflow: hidden;
		margin: 2rem 0;
		border-radius: 8px;

		display: flex;
		justify-content: space-between;
		align-items: center;
		height: 200px;
	}

	.header-logo {
		display: flex;
		flex-direction: column;
		align-items: center;

		padding: 0.5rem 1rem;
		border-radius: 4px;

		&--main {
			letter-spacing: 0.25;
			font-size: 2.3rem;
			font-weight: 400;
		}

		&--sub {
			font-size: 1rem;
			font-weight: 600;
		}
	}

	h2 {
		font-weight: 400;
		margin: 0;
		font-size: 1rem;
	}

	.vertical {
		width: 400px;
		&:first-child {
			margin-bottom: 1rem;
		}
	}

	datalist {
		display: flex;
		justify-content: space-between;
		width: 100%;
		font-size: 0.75rem;
		font-weight: 200;
		padding-top: 0.15rem;
	}

	.tickmark--text {
	}

	.tickmark--tick {
		position: relative;
		top: -18px;
		width: 1px;
		height: 18px;
		padding: 0;
		margin: 0;
		z-index: 1;
		background: var(--neutral-font-80);
	}
	input {
		width: 100%;
	}

	.range--value {
		font-size: 0.75rem;
		border-radius: 4px;
		padding: 0 0.25rem;
	}
</style>

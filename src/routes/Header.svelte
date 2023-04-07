<script>
	import { onMount } from 'svelte';
	import RangeInput from '../components/RangeInput.svelte';
	import { RadioStatic } from 'radio-color-system';
	let colors = [
		{ color: { h: 200, s: 12, l: 70 }, name: 'secondary' },
		{
			color: { h: 240, s: 24, l: 48 },
			name: 'primary'
		},
		{ color: { h: 342, s: 25, l: 61 }, name: 'tertiary' },
		{ color: { h: 270, s: 2, l: 57 }, name: 'neutral' }
	];
</script>

<RadioStatic {colors} async={true} />

<header class="primary-90">
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
	<div class="r-side">
		<div class="vertical-container">
			<RangeInput
				name="sat"
				header="Saturation"
				icon="vital_signs"
				bind:value={colors[1].color.s}
			/>
			<RangeInput name="light" header="Light" icon="light_mode" bind:value={colors[1].color.l} />
		</div>
		<div class="knob">
			<div class="knob-container neutral-70">
				<div class="primary-60 knob-button">
					<div class="knob-button--inner neutral-70 neutral-font-70">360°</div>
				</div>
			</div>
		</div>
	</div>
</header>

<style lang="scss">
	.r-side {
		display: flex;
		gap: 2rem;
		align-items: center;
		z-index: 1;
	}
	.vertical-container {
		display: flex;
		gap: 0.5rem;
		flex-direction: column;
	}

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
	.color {
		position: absolute;
		display: flex;
		top: -180px;
		left: 0px;
		transform: rotate(320deg);
		z-index: 0;

		&--item {
			width: 6em;
			height: 40rem;
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

	header {
		position: relative;
		overflow: hidden;
		margin: 2rem 0;
		border-radius: 8px;

		display: flex;
		justify-content: space-between;
		align-items: center;
		min-height: 200px;

		padding: 0 1rem;
	}

	.header-logo {
		display: flex;
		flex-direction: column;
		align-items: center;

		padding: 0.5rem 0;
		border-radius: 4px;

		&--main {
			font-weight: 400;
			font-size: 48px;
			letter-spacing: 0;
			z-index: 1;
		}

		&--sub {
			font-size: 20px;
			font-weight: 400;
			letter-spacing: 0;
			z-index: 1;
		}
	}
</style>

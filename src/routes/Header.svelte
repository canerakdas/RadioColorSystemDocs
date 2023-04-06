<script>
	import { onMount } from 'svelte';

	onMount(() => {
		const t = window.matchMedia && window.matchMedia('(prefers-color-scheme: dark)').matches;
	});
</script>

<div class="conta">
	<header>
		<div>
			<h1 class="header-logo">
				<span class="header-logo--main neutral-font-90">Radio</span>
				<span class="header-logo--sub neutral-font-90">Color System</span>
			</h1>
			<div class="colors">
				{#each [0, 10, 20, 30, 40, 50, 60, 70, 80, 90, 100] as codes}
					<div class={`primary-${codes} primary-font-${codes} color--item`} />
				{/each}
			</div>
		</div>
		<div class="vertical-container">
			<div class="vertical">
				<h2 class="neutral-font-70">Saturation</h2>
				<input class="sat" type="range" list="tickmark" min="0" max="100" value="100" />

				<datalist id="tickmark">
					{#each [0, 5, 10, 15, 20, 25, 30, 35, 40, 45, 50, 55, 60, 65, 70, 75, 80, 85, 90, 95, 100] as frequency}
						<option
							class={frequency % 10 === 0 ? 'neutral-font-90' : 'neutral-font-50'}
							value={frequency}
							label={frequency % 10 === 0 ? String(frequency) : '|'}
						/>
					{/each}
				</datalist>
			</div>
			<div class="vertical">
				<h2 class="neutral-font-70">Lightning</h2>
				<input class="sat" type="range" list="tickmark" min="0" max="100" value="50" />

				<datalist id="tickmark">
					{#each [0, 5, 10, 15, 20, 25, 30, 35, 40, 45, 50, 55, 60, 65, 70, 75, 80, 85, 90, 95, 100] as frequency}
						<option
							class={frequency % 10 === 0 ? 'neutral-font-90' : 'neutral-font-50'}
							value={frequency}
							label={frequency % 10 === 0 ? String(frequency) : '|'}
						/>
					{/each}
				</datalist>
			</div>
		</div>
		<div>
			<div class="casette neutral-50">primary</div>
		</div>
		<div class="knob">
			<div class="knob-container neutral-70">
				<div class="primary-50 knob-button">
					<div class="knob-button--inner neutral-70 neutral-font-70">360°</div>
				</div>
			</div>
		</div>
	</header>
</div>

<style lang="scss">
	.conta {
		width: 1024px;
		margin: 0 auto;
	}
	.speaker {
		margin: 2rem 0 0 0;
		display: flex;
		justify-content: space-between;
		align-items: center;
		border-radius: 2px;
		background-color: var(--primary-80);
		height: 3rem;
	}
	.speaker > svg > path {
		fill: var(--primary-50);
	}

	.casette {
		width: 200px;
		height: 66px;
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
			width: calc(6rem - 2px);
			height: calc(6rem - 2px);

			border-radius: 50%;
			display: flex;
			justify-content: center;
			align-items: center;
		}
	}

	input[type='range'] {
		-webkit-appearance: none;
		height: 0;
		background: var(--neutral-70);
		border-radius: 2px;
		border: 5px dashed var(--neutral-50);

		@media (prefers-dark-interface) {
			background: var(--neutral-dark-50);
		}
	}

	input[type='range']::-webkit-slider-thumb {
		position: relative;
		top: -0.75rem;
		-webkit-appearance: none;
		height: 20px;
		width: 40px;
		border-radius: 1rem;
		background: var(--primary-30);
		cursor: ew-resize;
		box-shadow: inset 0 0 0 2px var(--primary-30), inset 0 0 0 3px var(--neutral-70);
		transition: background 0.3s ease-in-out;
	}

	header {
		display: flex;
		justify-content: space-between;
		align-items: center;
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
		width: 500px;
	}

	datalist {
		display: flex;
		justify-content: space-between;
		width: 100%;
		font-size: 0.75rem;
		font-weight: 200;
		padding-top: 0.25rem;
	}

	.tickmark--text {
	}

	.tickmark--tick {
	}
	input {
		width: 100%;
	}

	.color--item {
		width: 20px;
	}
</style>

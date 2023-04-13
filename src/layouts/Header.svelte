<script>
	import { onMount, getContext } from 'svelte';

	import RangeInput from '$components/RangeInput.svelte';
	import HueKnob from '$components/HueKnob.svelte';

	let colors = getContext('colors');
	let color = $colors.find((color) => color.selected);
	let index = 0;

	$: {
		index = $colors.findIndex((color) => color.selected);
	}

	let kind = (color && color.name) || 'primary';
</script>

<header>
	<div class="header">
		<div>
			<h1 class="header--logo primary-font-90">
				<span class="mdc-typography--headline2">Radio</span>
				<span class="mdc-typography--headline4">Color System</span>
			</h1>
		</div>
		<div class="header--controls">
			<div class="header--range">
				<RangeInput
					name="sat"
					header="Saturation"
					icon="vital_signs"
					bind:value={$colors[index].color.s}
				/>
				<RangeInput
					name="light"
					header="Light"
					icon={$colors[index].color.l > 40 ? 'light_mode' : 'dark_mode'}
					bind:value={$colors[index].color.l}
				/>
			</div>
			<div>
				<div class="header--knob primary-font-90">
					<span class="material-symbols-outlined">palette</span>
					<div class="mdc-typography--headline6">Hue</div>
				</div>
				<HueKnob />
			</div>
		</div>
	</div>
	<div class="animation">
		<svg class="animation--water">
			<defs>
				<pattern
					id="water"
					width="55"
					height="41"
					patternUnits="userSpaceOnUse"
					patternTransform="scale(0.5) rotate(0)"
				>
					<path
						xmlns="http://www.w3.org/2000/svg"
						d="M29.5 37H0L2.22027e-06 41H33.5V12H17.5V25H9.5V4H44.5V41H54.5L54.5 37H48.5L48.5 0H5.5V29H21.5V16H29.5V37Z"
					/>
				</pattern>
			</defs>

			<rect width="100%" height="20px" fill="url(#water)" />
		</svg>
		<svg class="animation--tree">
			<defs>
				<pattern
					id="tree"
					width="160"
					height="312"
					patternUnits="userSpaceOnUse"
					patternTransform="scale(0.3) rotate(0)"
				>
					<path d="M41 117V129H37V113H64V136L3 178V171L58 133V117H41Z" />
					<path d="M41 69V81H37V65H64V88L3 130V123L58 85V69H41Z" />
					<path d="M41 22V34H37V18H64V41L3 83V76L58 38V22H41Z" />
					<path d="M0 43H3V185H6V305.5H154V311.5H6H0V43Z" />
					<path d="M160 6H86H0V0H160V6Z" />
					<path d="M119 117V129H123V113H96V136L157 178V171L102 133V117H119Z" />
					<path d="M119 69V81H123V65H96V88L157 130V123L102 85V69H119Z" />
					<path d="M119 22V34H123V18H96V41L157 83V76L102 38V22H119Z" />
					<path d="M160 43H157V185H154V311.5H160V43Z" />
					<path d="M121 200.5V188.5H117V204.5H144V181.5L83 139.5V146.5L138 184.5V200.5H121Z" />
					<path d="M121 248.5V236.5H117V252.5H144V229.5L83 187.5V194.5L138 232.5V248.5H121Z" />
					<path d="M121 295.5V283.5H117V299.5H144V276.5L83 234.5V241.5L138 279.5V295.5H121Z" />
					<path d="M39 200.5V188.5H43V204.5H16V181.5L77 139.5V146.5L22 184.5V200.5H39Z" />
					<path d="M39 248.5V236.5H43V252.5H16V229.5L77 187.5V194.5L22 232.5V248.5H39Z" />
					<path d="M39 295.5V283.5H43V299.5H16V276.5L77 234.5V241.5L22 279.5V295.5H39Z" />
					<path d="M83 274.5H77V132.5H74V6H86V132.5H83V274.5Z" />
				</pattern>
			</defs>

			<rect width="100%" height="162" fill="url(#tree)" />
		</svg>
	</div>
</header>

<style lang="scss">
	header {
		display: flex;
		flex-direction: column;
		gap: 4rem;
		padding: 4rem 1rem 1rem 1rem;
		overflow: hidden;
		margin: 2rem 0;
		border-radius: 1rem;
		background: linear-gradient(270deg, var(--neutral-80), var(--primary-80));
		background-size: 400% 400%;
		position: relative;

		@media (prefers-reduced-motion: no-preference) {
			animation: backgroundGradient 32s cubic-bezier(0.25, 0.46, 0.45, 0.94) infinite;
		}

		@media (max-width: 768px) {
			padding: 1rem;
		}
	}

	.header {
		display: flex;
		justify-content: space-between;

		@media (max-width: 768px) {
			flex-direction: column;
		}
	}

	.header--controls {
		display: flex;
		gap: 4rem;
		align-items: center;
		z-index: 1;

		@media (max-width: 768px) {
			flex-direction: column;
			align-items: flex-end;
			gap: 2rem;
		}
	}

	.header--range {
		display: flex;
		gap: 2rem;
		flex-direction: column;
		width: 24rem;

		@media (max-width: 768px) {
			width: 100%;
		}
	}

	.header--knob {
		display: flex;
		gap: 0.5rem;
		align-items: center;
		margin-left: 0.5rem;
	}

	.header--logo {
		display: flex;
		flex-direction: column;
		align-items: start;

		padding: 0.5rem 0;
	}

	.animation {
		position: relative;
		overflow: hidden;
		border-radius: 0 0 1rem 1rem;
		border: 2px solid var(--primary-50);

		display: flex;
		flex-direction: column;
		gap: 4px;

		@media (max-width: 768px) {
			display: none;
		}
	}

	.animation--tree {
		width: calc(100% + 48px);
		height: 92px;
		fill: var(--primary-50);

		@media (prefers-reduced-motion: no-preference) {
			animation: scrollToLeft 16s linear infinite;
		}
	}

	.animation--water {
		height: 20px;
		width: calc(100% + 27px);
		fill: var(--primary-50);

		padding-top: 4px;
		position: relative;
		left: -27px;

		@media (prefers-reduced-motion: no-preference) {
			animation: scrollToRight 16s linear infinite;
		}
	}

	@keyframes scrollToRight {
		100% {
			transform: translateX(27px);
		}
	}

	@keyframes scrollToLeft {
		100% {
			transform: translateX(-48px);
		}
	}

	@keyframes backgroundGradient {
		0% {
			background-position: 0% 50%;
		}
		50% {
			background-position: 100% 50%;
		}
		100% {
			background-position: 0% 50%;
		}
	}
</style>

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
	<div class="header--redirect">
		<a
			target="_blank"
			href="https://www.npmjs.com/package/radio-color-system"
			alt="NPM page of Radio color system"
			aria-label="NPM page of Radio color system"
		>
			<svg viewBox="0 0 780 250" height="16">
				<path
					d="M240,250h100v-50h100V0H240V250z M340,50h50v100h-50V50z M480,0v200h100V50h50v150h50V50h50v150h50V0H480z M0,200h100V50h50v150h50V0H0V200z"
				/>
			</svg>
		</a>
		<a
			target="_blank"
			href="https://github.com/canerakdas/RadioColorSystem"
			alt="Github page of Radio color system"
			aria-label="Github page of Radio color system"
		>
			<svg height="24" viewBox="0 0 45 16" width="67.2">
				<path
					d="M8.81 7.35v5.74c0 .04-.01.11-.06.13 0 0-1.25.89-3.31.89-2.49 0-5.44-.78-5.44-5.92S2.58 1.99 5.1 2c2.18 0 3.06.49 3.2.58.04.05.06.09.06.14L7.94 4.5c0 .09-.09.2-.2.17-.36-.11-.9-.33-2.17-.33-1.47 0-3.05.42-3.05 3.73s1.5 3.7 2.58 3.7c.92 0 1.25-.11 1.25-.11v-2.3H4.88c-.11 0-.19-.08-.19-.17V7.35c0-.09.08-.17.19-.17h3.74c.11 0 .19.08.19.17Zm35.85 2.33c0 3.43-1.11 4.41-3.05 4.41-1.64 0-2.52-.83-2.52-.83s-.04.46-.09.52c-.03.06-.08.08-.14.08h-1.48c-.1 0-.19-.08-.19-.17l.02-11.11c0-.09.08-.17.17-.17h2.13c.09 0 .17.08.17.17v3.77s.82-.53 2.02-.53l-.01-.02c1.2 0 2.97.45 2.97 3.88ZM27.68 2.43c.09 0 .17.08.17.17v11.11c0 .09-.08.17-.17.17h-2.13c-.09 0-.17-.08-.17-.17l.02-4.75h-3.31v4.75c0 .09-.08.17-.17.17h-2.13c-.08 0-.17-.08-.17-.17V2.6c0-.09.08-.17.17-.17h2.13c.09 0 .17.08.17.17v4.09h3.31V2.6c0-.09.08-.17.17-.17Zm8.26 3.64c.11 0 .19.08.19.17l-.02 7.47c0 .09-.06.17-.17.17H34.6c-.07 0-.14-.04-.16-.09-.03-.06-.08-.45-.08-.45s-1.13.77-2.52.77c-1.69 0-2.92-.55-2.92-2.75V6.25c0-.09.08-.17.17-.17h2.14c.09 0 .17.08.17.17V11c0 .75.22 1.09.97 1.09s1.3-.39 1.3-.39V6.26c0-.11.06-.19.17-.19Zm-17.406 5.971h.005a.177.177 0 0 1 .141.179v1.5c0 .07-.03.14-.09.16-.1.05-.74.22-1.27.22-1.16 0-2.86-.25-2.86-2.69V8.13h-1.11c-.09 0-.17-.08-.17-.19V6.58c0-.08.05-.15.13-.17.07-.01 1.16-.28 1.16-.28V3.96c0-.08.05-.13.14-.13h2.16c.09 0 .14.05.14.13v2.11h1.59c.08 0 .16.08.16.17v1.7c0 .11-.07.19-.16.19h-1.59v3.131c0 .47.27.83 1.05.83.247 0 .481-.049.574-.05ZM12.24 6.06c.09 0 .17.08.17.17v7.37c0 .18-.05.27-.25.27h-1.92c-.17 0-.3-.07-.3-.27V6.26c0-.11.08-.2.17-.2Zm29.99 3.78c0-1.81-.73-2.05-1.5-1.97-.6.04-1.08.34-1.08.34v3.52s.49.34 1.22.36c1.03.03 1.36-.34 1.36-2.25ZM11.19 2.68c.75 0 1.36.61 1.36 1.38 0 .77-.61 1.38-1.36 1.38-.77 0-1.38-.61-1.38-1.38 0-.77.61-1.38 1.38-1.38Zm7.34 9.35v.001l.01.01h-.001l-.005-.001v.001c-.009-.001-.015-.011-.024-.011Z"
				/>
			</svg>
		</a>
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

		span {
			width: 1.5rem;
			height: 1.5rem;
		}
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

	.header--redirect {
		display: flex;
		align-items: flex-end;
		gap: 0.5rem;

		position: absolute;
		z-index: 3;
		right: 1rem;
		bottom: 8.8rem;
		@media (max-width: 768px) {
			left: 1rem;
			bottom: 1rem;
		}

		svg {
			fill: var(--primary-font-90);
			padding: 1rem 0 0 0;
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

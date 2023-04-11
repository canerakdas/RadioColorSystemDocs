<script>
	import { onMount } from 'svelte';
	import RangeInput from '../components/RangeInput.svelte';
	import { RadioStatic } from 'radio-color-system';
	export let index = 1;

	let colors = [
		{ color: { h: 230, s: 20, l: 50 }, name: 'secondary' },
		{
			color: { h: 34, s: 24, l: 48 },
			name: 'primary'
		},
		{ color: { h: 342, s: 25, l: 61 }, name: 'tertiary' },
		{ color: { h: 270, s: 2, l: 57 }, name: 'neutral' }
	];

	let draw = () => {};

	$: {
		colors, draw();
	}

	onMount(() => {
		const canvas = document.getElementById('knobCanvas');
		const ctx = canvas.getContext('2d');

		// Define the position of the knob's center
		const centerX = canvas.width / 2;
		const centerY = canvas.height / 2;

		// Define the radius of the knob
		const radius = 90;

		// Define the angle of the knob (in radians)
		let angle = (colors[index].color.h * Math.PI) / 180;

		// Draw the knob
		const drawKnob = () => {
			// Clear the canvas
			ctx.clearRect(0, 0, canvas.width, canvas.height);

			// Draw the knob's background
			ctx.beginPath();
			ctx.arc(centerX, centerY, radius - 20, 0, Math.PI * 2);
			let color = getComputedStyle(document.body).getPropertyValue('--neutral-70');
			let text = getComputedStyle(document.body).getPropertyValue('--primary-font-80');
			let primary = getComputedStyle(document.body).getPropertyValue('--primary-50');

			ctx.strokeStyle = primary;
			ctx.fillStyle = text;
			ctx.fill();

			// Draw the knob's indicator
			ctx.beginPath();
			ctx.moveTo(centerX, centerY);
			ctx.lineTo(
				centerX + Math.cos(angle - Math.PI / 2) * (radius - 30),
				centerY + Math.sin(angle - Math.PI / 2) * (radius - 30)
			);
			ctx.lineWidth = 4;
			ctx.lineCap = 'round';

			ctx.stroke();

			ctx.strokeStyle = primary;

			ctx.strokeStyle = text;

			// Draw lines at every 10 degrees
			for (let i = 0; i < 8; i++) {
				const angle = (i * 45 * Math.PI) / 180;
				const x1 = centerX + Math.cos(angle) * radius;
				const y1 = centerY + Math.sin(angle) * radius;
				const x2 = centerX + Math.cos(angle) * (radius - 7);
				const y2 = centerY + Math.sin(angle) * (radius - 7);
				ctx.lineWidth = 2;
				ctx.beginPath();
				ctx.moveTo(Number(Math.ceil(x1).toFixed(2)), Number(Math.ceil(y1).toFixed(2)));
				ctx.lineTo(Number(Math.ceil(x2).toFixed(2)), Number(Math.ceil(y2).toFixed(2)));
				ctx.stroke();
			}

			// Calculate the current angle in degrees from 0 to 360
			const degree = (angle * 180) / Math.PI;

			colors[index].color.h = parseInt(degree < 0 ? 360 + degree : degree);
		};

		// Update the angle of the knob when the mouse is dragged
		canvas.addEventListener('mousedown', (event) => {
			const rect = canvas.getBoundingClientRect();
			const mouseX = event.clientX - rect.left;
			const mouseY = event.clientY - rect.top;

			if (Math.sqrt((mouseX - centerX) ** 2 + (mouseY - centerY) ** 2) <= radius) {
				canvas.addEventListener('mousemove', dragKnob);
			}
		});

		// Stop updating the angle of the knob when the mouse is released
		canvas.addEventListener('mouseup', () => {
			canvas.removeEventListener('mousemove', dragKnob);
		});

		// Update the angle of the knob when it is touched and dragged
		canvas.addEventListener('touchstart', (event) => {
			const rect = canvas.getBoundingClientRect();
			const touchX = event.touches[0].clientX - rect.left;
			const touchY = event.touches[0].clientY - rect.top;

			if (Math.sqrt((touchX - centerX) ** 2 + (touchY - centerY) ** 2) <= radius) {
				canvas.addEventListener('touchmove', dragKnob);
			}
			document.body.style.overflow = 'hidden';
		});

		// Stop updating the angle of the knob when the touch is released
		canvas.addEventListener('touchend', () => {
			canvas.removeEventListener('touchmove', dragKnob);
			document.body.style.overflow = 'initial';
		});

		// Update the angle of the knob based on the mouse position
		function dragKnob(event) {
			const rect = canvas.getBoundingClientRect();

			if (event.touches) {
				const touchX = event.touches[0].clientX - rect.left;
				const touchY = event.touches[0].clientY - rect.top;

				angle = Math.atan2(touchY - centerY, touchX - centerX) + Math.PI / 2;
			} else {
				const mouseX = event.clientX - rect.left;
				const mouseY = event.clientY - rect.top;

				angle = Math.atan2(mouseY - centerY, mouseX - centerX) + Math.PI / 2;
			}

			drawKnob();
		}

		draw = drawKnob;
	});
</script>

<RadioStatic {colors} async={true} />

<header class="primary-90">
	<div class="border" />
	<div class="contr">
		<div>
			<h1 class="header-logo">
				<span class="header-logo--main primary-font-90 mdc-typography--headline2">Radio</span>
				<span class="header-logo--sub primary-font-90 mdc-typography--headline4">Color System</span>
			</h1>
		</div>
		<div class="r-side">
			<div class="vertical-container">
				<RangeInput
					name="sat"
					header="Saturation"
					icon="vital_signs"
					bind:value={colors[index].color.s}
				/>
				<RangeInput
					name="light"
					header="Light"
					icon={colors[index].color.l > 40 ? 'light_mode' : 'dark_mode'}
					bind:value={colors[index].color.l}
				/>
			</div>
			<div>
				<div class="knob--header primary-font-90">
					<span class="material-symbols-outlined">palette</span>
					<div class="mdc-typography--headline6">Hue</div>
				</div>
				<canvas id="knobCanvas" width="200" height="200" />
			</div>
		</div>
	</div>
	<div class="hfooter">
		<svg class="water">
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
		<svg class="tree" xmlns="http://www.w3.org/2000/svg" width="100%" height="100%" fill="black">
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
	.hfooter {
		position: relative;
		overflow: hidden;
		border-radius: 0 0 1rem 1rem;
		border: 2px solid var(--primary-50);

		display: flex;
		flex-direction: column;
		gap: 4px;
	}
	.contr {
		display: flex;
		justify-content: space-between;
	}
	.knob--header {
		display: flex;
		gap: 0.5rem;
		align-items: center;
		margin-left: 0.5rem;
	}
	#knobCanvas {
		cursor: pointer;
	}
	.r-side {
		display: flex;
		gap: 4rem;
		align-items: center;
		z-index: 1;
	}
	.vertical-container {
		display: flex;
		gap: 2rem;
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
			width: 3rem;
			height: 40rem;
		}
	}
	.knob {
	}

	header {
		display: flex;
		flex-direction: column;
		gap: 4rem;

		overflow: hidden;
		margin: 2rem 0;
		border-radius: 1rem;
		background: linear-gradient(270deg, var(--neutral-80), var(--primary-80));
		background-size: 400% 400%;
		position: relative;

		animation: AnimationName 32s cubic-bezier(0.25, 0.46, 0.45, 0.94) infinite;

		@keyframes AnimationName {
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
		padding: 1rem;
	}

	.header-logo {
		display: flex;
		flex-direction: column;
		align-items: start;

		padding: 0.5rem 0;
		border-radius: 4px;

		&--main {
			z-index: 1;
		}

		&--sub {
			z-index: 1;
		}
	}

	.tree {
		fill: var(--primary-50);
		height: 92px;
		animation: scrolll 16s linear infinite;
		width: calc(100% + 48px);
	}

	.water {
		height: 20px;
		width: calc(100% + 27px);
		fill: var(--primary-50);
		animation: scrollr 16s linear infinite;

		padding-top: 4px;
		position: relative;
		left: -27px;
	}

	@keyframes scrollr {
		100% {
			transform: translateX(27px);
		}
	}

	@keyframes scrolll {
		100% {
			transform: translateX(-48px);
		}
	}
</style>

<script>
	import { onMount } from 'svelte';
	import RangeInput from '../components/RangeInput.svelte';
	import { RadioStatic } from 'radio-color-system';
	let colors = [
		{ color: { h: 200, s: 12, l: 70 }, name: 'secondary' },
		{
			color: { h: 30, s: 24, l: 48 },
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
		ctx.translate(0.5, 0.5);

		// Define the position of the knob's center
		const centerX = canvas.width / 2;
		const centerY = canvas.height / 2;

		// Define the radius of the knob
		const radius = 60;

		// Define the angle of the knob (in radians)
		let angle = (colors[1].color.h * Math.PI) / 180;

		// Draw the knob
		const drawKnob = () => {
			// Clear the canvas
			ctx.clearRect(0, 0, canvas.width, canvas.height);

			// Draw the knob's background
			ctx.beginPath();
			ctx.arc(centerX, centerY, radius - 10, 0, Math.PI * 2);
			let color = getComputedStyle(document.body).getPropertyValue('--neutral-70');
			let text = getComputedStyle(document.body).getPropertyValue('--neutral-font-80');
			let primary = getComputedStyle(document.body).getPropertyValue('--primary-50');

			ctx.strokeStyle = text;
			ctx.fillStyle = primary;
			ctx.fill();

			// Draw the knob's indicator
			ctx.beginPath();
			ctx.moveTo(centerX, centerY);
			ctx.lineTo(
				centerX + Math.cos(angle - Math.PI / 2) * (radius - 10),
				centerY + Math.sin(angle - Math.PI / 2) * (radius - 10)
			);
			ctx.lineWidth = 4;
			ctx.lineCap = 'round';

			ctx.stroke();

			ctx.beginPath();
			ctx.arc(centerX, centerY, radius - 10, 0, Math.PI * 2);
			ctx.lineWidth = 2;

			ctx.stroke();

			// Draw lines at every 10 degrees
			for (let i = 0; i < 18; i++) {
				const angle = (i * 20 * Math.PI) / 180;
				const x1 = centerX + Math.cos(angle) * radius;
				const y1 = centerY + Math.sin(angle) * radius;
				const x2 = centerX + Math.cos(angle) * (radius - 5);
				const y2 = centerY + Math.sin(angle) * (radius - 5);
				ctx.lineWidth = 1;
				ctx.beginPath();
				ctx.moveTo(Number(Math.ceil(x1).toFixed(2)), Number(Math.ceil(y1).toFixed(2)));
				ctx.lineTo(Number(Math.ceil(x2).toFixed(2)), Number(Math.ceil(y2).toFixed(2)));
				ctx.stroke();
			}

			// Calculate the current angle in degrees from 0 to 360
			const degree = (angle * 180) / Math.PI;

			colors[1].color.h = parseInt(degree < 0 ? 360 + degree : degree);
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
	<div>
		<h1 class="header-logo">
			<span class="header-logo--main primary-font-70">Radio</span>
			<span class="header-logo--sub primary-font-70">Color System</span>
		</h1>
		<div class="color">
			{#each [50, 60, 70, 80, 90] as codes}
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
			<RangeInput
				name="light"
				header="Light"
				icon={colors[1].color.l > 40 ? 'light_mode' : 'dark_mode'}
				bind:value={colors[1].color.l}
			/>
		</div>
		<canvas id="knobCanvas" width="150" height="150" />
	</div>
</header>

<style lang="scss">
	#knobCanvas {
		cursor: pointer;
	}
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
			width: 3rem;
			height: 40rem;
		}
	}
	.knob {
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

		background: linear-gradient(130deg, var(--primary-80) 0%, var(--neutral-80) 100%);
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

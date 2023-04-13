<script>
	// Todo: remove color logic from this component
	import { onMount, getContext } from 'svelte';

	import RangeInput from '$components/RangeInput.svelte';

	let colors = getContext('colors');
	let color = $colors.find((color) => color.selected);
	let index = 0;
	let draw = () => {};

	$: {
		index = $colors.findIndex((color) => color.selected);
		draw($colors[index].color.h);
	}

	let angle = (color.color.h * Math.PI) / 180;

	let kind = (color && color.name) || 'primary';

	onMount(() => {
		const canvas = document.getElementById('knobCanvas');
		const ctx = canvas.getContext('2d');

		// Define the position of the knob's center
		const centerX = canvas.width / 2;
		const centerY = canvas.height / 2;
		let active = color;
		// Define the radius of the knob
		const radius = 90;

		// Define the angle of the knob (in radians)

		// Draw the knob
		const drawKnob = (hue) => {
			if (hue) {
				$colors[index].color.h = hue;
				angle = (hue * Math.PI) / 180;
				kind = $colors[index].name;
			}
			// Clear the canvas
			ctx.clearRect(0, 0, canvas.width, canvas.height);

			// Draw the knob's background
			ctx.beginPath();
			ctx.arc(centerX, centerY, radius - 20, 0, Math.PI * 2);
			let color = getComputedStyle(document.body).getPropertyValue('--neutral-70');
			let text = getComputedStyle(document.body).getPropertyValue(`--primary-font-80`);
			let primary = getComputedStyle(document.body).getPropertyValue(`--primary-50`);

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
			$colors[index].color.h = parseInt(degree < 0 ? 360 + degree : degree);
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
		canvas.addEventListener(
			'touchstart',
			(event) => {
				const rect = canvas.getBoundingClientRect();
				const touchX = event.touches[0].clientX - rect.left;
				const touchY = event.touches[0].clientY - rect.top;

				if (Math.sqrt((touchX - centerX) ** 2 + (touchY - centerY) ** 2) <= radius) {
					canvas.addEventListener('touchmove', dragKnob);
				}
				document.body.style.overflow = 'hidden';
			},
			{ passive: true }
		);

		// Stop updating the angle of the knob when the touch is released
		canvas.addEventListener(
			'touchend',
			() => {
				canvas.removeEventListener('touchmove', dragKnob);
				document.body.style.overflow = 'initial';
			},
			{ passive: true }
		);

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

<canvas id="knobCanvas" width="200" height="200" />

<style lang="scss">
	canvas {
		cursor: pointer;
	}
</style>

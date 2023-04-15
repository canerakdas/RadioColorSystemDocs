<script>
	import { RadioActive } from 'radio-color-system';
	import Palette from '$sections/Palette.svelte';

	// Docs
	import Color from '$sections/docs/Color.svelte';
	import ColorOption from '$sections/docs/ColorOption.svelte';
	import ColorVariant from '$sections/docs/ColorVariant.svelte';
	import RadioActiveDocs from '$sections/docs/RadioActive.svelte';
	import RadioStaticDocs from '$sections/docs/RadioStatic.svelte';
	import Usage from '$sections/Usage.svelte';
	import ActiveUsage from '$sections/ActiveUsage.svelte';
	import RadioActiveExamples from '$sections/example/RadioActive.svelte';

	import Card from '$components/Card.svelte';

	let index = 1;
	let images = [1, 2, 3];
	let target = `#image${index}`;
</script>

<Palette />
<Usage />
<RadioActiveExamples />
<ActiveUsage />
<RadioActiveDocs />
<RadioStaticDocs />
<ColorVariant />
<ColorOption />
<Color />

<script>
	export let name;
	export let value;
	export let checked;
	export let label;
</script>

<div class="radio-input">
	<input type="radio" id={value} {name} bind:value {checked} />
	<label for={value}>{label}</label>
</div>

<style lang="scss">
	.radio-input {
		display: flex;
		align-items: center;
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
</style>

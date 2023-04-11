<script>
	export let name;
	export let value;
	export let checked;
	export let label;
	export let click;
</script>

<div class="radio-input">
	<input type="radio" id={value} {name} bind:value {checked} />
	<label
		for={value}
		on:click={() => {
			click();
		}}
	>
		<div class="mdc-typography--button">
			{label}
		</div>
	</label>
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
		align-items: flex-start;
		cursor: pointer;
		padding: 0 2rem;
		border-radius: 50px;
		flex-direction: column;
		color: var(--neutral-font-80);
		margin: 0.5rem 0;
		transition: box-shadow 0.2s ease-in-out, background-color 0.2s ease-in-out;
	}

	label:hover {
		box-shadow: 0 0 0 2px var(--neutral-80), 0 0 0 4px var(--neutral-50);
	}

	input[type='radio']:checked + label {
		box-shadow: 0 0 0 2px var(--neutral-80), 0 0 0 4px var(--primary-50);
		background-color: var(--primary-70);
		color: var(--primary-font-70);
	}

	.caption {
		margin-bottom: 0.25rem;
	}
</style>

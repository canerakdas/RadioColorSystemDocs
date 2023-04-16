<script>
	export let name;
	export let type;
	export let defaultValue;
	export let description;
	export let kind = 'neutral';
	export let element = '';
	export let optional = false;
	export let href = '';
	export let alt = '';
	export let sub = false;

	import Tag from '$components/Tag.svelte';
	export let id = `${element}-${name}`;

	const propertyClass = sub ? 'property property--sub' : 'property';
</script>

<div class={propertyClass}>
	<div class="header">
		<h3 class="mdc-typography--headline5">
			{#if href}
				<a {href} {alt}>{name}</a>
			{:else if sub === false}
				<a alt="{name} Property" class="header--link" href="#{id}">
					{name}
					<span class="material-symbols-outlined {kind}-80 {kind}-font-80"> link </span>
				</a>
			{/if}
		</h3>
		<div class="header--type">
			{#if type === 'boolean'}
				<span class="material-symbols-outlined"> check_box </span>
			{:else if type === 'string'}
				<span class="material-symbols-outlined"> format_quote </span>
			{:else if type === 'object' || type === 'Color' || type === 'ColorOption'}
				<span class="material-symbols-outlined"> data_object </span>
			{:else if type.indexOf('[]') >= 0}
				<span class="material-symbols-outlined"> data_array </span>
			{:else if type === 'number'}
				<span class="material-symbols-outlined"> 123 </span>
			{:else if type === 'function' || type === 'ColorVariant'}
				<span class="material-symbols-outlined"> function </span>
			{/if}
			<span class="mdc-typography--caption">{type}</span>

			{#if optional}
				<Tag {kind}>Optional</Tag>
			{/if}
		</div>
	</div>
	{#if description}
		<p class="mdc-typography--body1">{description}</p>
	{/if}
	{#if defaultValue}
		<pair>
			<key class="mdc-typography--subtitle1">Default</key>
			<value class="mdc-typography--body2">"{defaultValue}"</value>
		</pair>
	{/if}
	<hr class="{kind}-80" />
	<slot />
</div>

<style lang="scss">
	hr {
		border: none;
		height: 1px;
		margin-top: 1rem;
		width: 100%;
	}

	.property {
		position: relative;

		&:hover {
			.header--link span {
				opacity: 1;

				@media (prefers-reduced-motion: no-preference) {
					transition: all 0.2s ease-in-out;
				}
			}
		}
	}

	.property--sub {
		margin-left: 1rem;
	}

	.header {
		display: flex;
		flex-direction: column;
		align-items: flex-start;

		a {
			color: currentColor;
		}
	}

	.header--type {
		display: flex;
		flex-direction: row;
		align-items: center;
		gap: 0.5rem;
	}

	.header--link {
		color: currentColor;
		text-decoration: none;
		display: flex;
		gap: 0.5rem;
		align-items: center;

		span {
			opacity: 0;
			padding: 0.25rem;
			border-radius: 0.25rem;

			@media (prefers-reduced-motion: no-preference) {
				transition: all 0.2s ease-in-out;
			}
		}
	}

	pair {
		display: flex;
		gap: 0.25rem;
		align-items: center;
	}

	pair value {
		padding: 0 0.25rem;
		border-radius: 2px;
		font-family: 'Source Code Pro', monospace;
	}
</style>

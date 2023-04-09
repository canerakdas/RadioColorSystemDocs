<script>
	import Header from './Header.svelte';
	import Tag from './Tag.svelte';

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

	export let id = `${element}-${name}`;
</script>

<div class={sub ? 'attribute attribute--sub' : 'attribute'}>
	<div class="header">
		<h4 class="mdc-typography--headline5">
			{#if href}
				<a {href} {alt}>{name}</a>
			{:else}
				{name}
			{/if}
		</h4>
		<div class="header--attribute">
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
	<div class={`seperator ${kind}-80`} />
	<slot />
	{#if sub === false && href === ''}
		<a alt={`${name} Attribute`} class="header--link" href={`#${id}`}>
			<span class={`material-symbols-outlined ${kind}-90 ${kind}-font-90`}> link </span>
		</a>
	{/if}
</div>

<style lang="scss">
	.seperator {
		height: 1px;
		margin-top: 1rem;
		width: 100%;
	}

	.attribute {
		position: relative;
		padding: 0 1rem 1rem 1rem;

		&:hover {
			.header--link {
				transition: all 0.2s ease-in-out;
				opacity: 1;
			}
		}
	}

	.attribute--sub {
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
		margin-left: 0.5rem;
		font-family: 'Source Code Pro', monospace;
	}

	.header--attribute {
		display: flex;
		flex-direction: row;
		align-items: center;
		gap: 0.5rem;
	}

	.header--link {
		color: currentColor;
		text-decoration: none;
		position: absolute;
		left: -3rem;
		top: -0.25rem;
		display: flex;
		opacity: 0;
		padding: 0.25rem;
		height: 100%;
		width: 2.5rem;

		span {
			width: 32px;
			height: 32px;
			font-size: 24px;
			display: flex;
			align-items: center;
			justify-content: center;

			border-radius: 4px;
			margin-top: 2rem;
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

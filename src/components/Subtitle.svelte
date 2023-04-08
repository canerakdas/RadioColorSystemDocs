<script>
	import Tag from './Tag.svelte';
	export let tag = '';
	export let icon = '';
</script>

<div class="neutral-font-80 subtitle">
	{#if icon !== ''}
		<span class="material-symbols-outlined subtitle--icon">{icon}</span>
	{/if}
	<slot />
	{#if tag !== ''}
		<Tag>{tag}</Tag>
	{/if}
</div>

<style lang="scss">
	.subtitle {
		display: flex;
		align-items: center;
		gap: 0.25rem;

		font-weight: 400;
		margin: 0;
		font-size: 1rem;
		letter-spacing: 0.009rem;
	}

	.subtitle--icon {
		font-size: 1rem;
	}
</style>

<script>
	export let kind = 'primary';

	let classes = {
		primary: 'tag primary-80 primary-font-80',
		secondary: 'tag secondary-80 secondary-font-80',
		tertiary: 'tag tertiary-80 tertiary-font-80',
		neutral: 'tag neutral-80 neutral-font-80'
	};
</script>

<div class={classes[kind]}><slot /></div>

<style lang="scss">
	.tag {
		font-size: 0.75rem;
		border-radius: 4px;
		padding: 0 0.25rem;
		line-height: 1rem;
	}
</style>

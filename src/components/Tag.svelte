<script>
	export let kind = 'primary';
</script>

<div class="{kind}-70 {kind}-font-70 mdc-typography--caption tag"><slot /></div>

<style lang="scss">
	.tag {
		border-radius: 4px;
		padding: 4px 8px;
	}
</style>

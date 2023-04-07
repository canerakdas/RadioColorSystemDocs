<script>
	import Header from './Header.svelte';
</script>

<div class="container">
	<Header />
	<div class="card secondary-80 secondary-font-80">
		<h3>
			<span class="secondary-80 secondary-font-80">Header</span>
			<span class="underline">not header</span>
		</h3>
		<p>
			Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla mollis aliquet erat eget
			facilisis. Phasellus fermentum semper ante dictum vehicula. Class aptent taciti sociosqu ad
			litora torquent per conubia nostra, per inceptos himenaeos. Etiam sit amet ligula risus. Donec
			et pulvinar nibh. Etiam augue odio, auctor eget ornare sit amet, sodales eu orci. Praesent
			hendrerit feugiat libero vel vulputate. Maecenas id molestie felis. Praesent convallis sapien
			est, at gravida metus viverra in. Nunc blandit, metus a rhoncus mattis, nibh ex tristique
			odio, eget accumsan risus ligula sed sem. Mauris hendrerit ultricies accumsan. Donec dictum
			diam ac libero facilisis dictum sed et sem.
		</p>
	</div>
	<div class="card neutral-80">asdfs</div>

	<div class="card secondary-80 secondary-font-80">
		<h3>
			<span class="secondary-80 secondary-font-80">Header</span>
			<span class="underline">not header</span>
		</h3>
		<p>
			Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla mollis aliquet erat eget
			facilisis. Phasellus fermentum semper ante dictum vehicula. Class aptent taciti sociosqu ad
			litora torquent per conubia nostra, per inceptos himenaeos. Etiam sit amet ligula risus. Donec
			et pulvinar nibh. Etiam augue odio, auctor eget ornare sit amet, sodales eu orci. Praesent
			hendrerit feugiat libero vel vulputate. Maecenas id molestie felis. Praesent convallis sapien
			est, at gravida metus viverra in. Nunc blandit, metus a rhoncus mattis, nibh ex tristique
			odio, eget accumsan risus ligula sed sem. Mauris hendrerit ultricies accumsan. Donec dictum
			diam ac libero facilisis dictum sed et sem.
		</p>
	</div>
	<div class="card primary-80 primary-font-80">
		<h3>
			<span class="primary-80 primary-font-80">Header</span>
			<span class="underline">not header</span>
		</h3>
		<p>
			Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla mollis aliquet erat eget
			facilisis. Phasellus fermentum semper ante dictum vehicula. Class aptent taciti sociosqu ad
			litora torquent per conubia nostra, per inceptos himenaeos. Etiam sit amet ligula risus. Donec
			et pulvinar nibh. Etiam augue odio, auctor eget ornare sit amet, sodales eu orci. Praesent
			hendrerit feugiat libero vel vulputate. Maecenas id molestie felis. Praesent convallis sapien
			est, at gravida metus viverra in. Nunc blandit, metus a rhoncus mattis, nibh ex tristique
			odio, eget accumsan risus ligula sed sem. Mauris hendrerit ultricies accumsan. Donec dictum
			diam ac libero facilisis dictum sed et sem.
		</p>
	</div>
</div>

<style lang="scss">
	.card {
		border-radius: 0.5rem;
		padding: 1rem;
		margin: 2rem auto;
		p {
			color: currentColor;
		}
	}

	h3 {
		margin: 0;
		padding: 0;
		display: flex;
		flex-direction: column;
		font-size: 2rem;
		font-weight: 300;
	}

	.underline {
		text-decoration: line-through;
		font-size: 1rem;
	}

	.container {
		margin: auto;
		padding: 0 1rem;

		@media (min-width: 1281px) {
			max-width: 1280px;
		}

		@media (min-width: 1024) {
			max-width: 1024px;
		}
	}
</style>

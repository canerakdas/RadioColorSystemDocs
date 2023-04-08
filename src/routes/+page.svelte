<script>
	import Header from './Header.svelte';
	import Card from '../components/Card.svelte';
	import RadioInput from '../components/RadioInput.svelte';
</script>

<div class="container">
	<Header />
	<div class="neutral-80 test">
		<fieldset>
			<RadioInput id="huey" name="a" value="huey" checked label="Primary Color" />
			<RadioInput id="dewey" name="a" value="dewey" label="Secondary Color" />
			<RadioInput id="c" name="a" value="c" label="Tertiary Color" />
			<RadioInput id="d" name="a" value="d" label="Neutral" />
		</fieldset>
	</div>
	<div class="primary-0 test">
		<div class="hece">
			{#each [0, 10, 20, 30, 40, 50, 60, 70, 80, 90, 100] as codes}
				<div class={`primary-${codes} primary-font-${codes} hehe`}>
					{codes}
				</div>
			{/each}
		</div>
	</div>
	<div class="card secondary-90 secondary-font-90">
		<h3>
			<span class="secondary-90 secondary-font-90">Header</span>
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

	<div class="card secondary-90 secondary-font-90">
		<h3>
			<span class="secondary-90 secondary-font-90">Header</span>
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
	.test {
		margin: 0;
		border-radius: 4px;
		display: flex;
		justify-content: space-between;
		overflow: hidden;
	}

	.hehe {
		width: 3rem;
		height: 3rem;
		font-size: 14px;
		display: flex;
		align-items: flex-start;
		justify-content: flex-end;
		padding: 4px;
	}

	.hece {
		display: flex;
	}

	fieldset {
		display: flex;
		gap: 1rem;
		border: none;
		padding: 0 1rem;
		margin: 0;
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

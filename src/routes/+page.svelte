<script>
	import Header from './Header.svelte';
	import Card from '../components/Card.svelte';
	import RadioInput from '../components/RadioInput.svelte';
	import Subtitle from '../components/Subtitle.svelte';
</script>

<div class="container">
	<Header />
	<div class="attr">
		<div class="neutral-80 test">
			<div class="at neutral-font-80">
				<span class="material-symbols-outlined"> format_paint </span>
				Colors
			</div>
			<fieldset>
				<RadioInput id="huey" name="a" value="huey" checked label="Primary Color" />
				<RadioInput id="dewey" name="a" value="dewey" label="Secondary Color" />
				<RadioInput id="c" name="a" value="c" label="Tertiary Color" />
				<RadioInput id="d" name="a" value="d" label="Neutral" />
			</fieldset>
		</div>
		<div class="primary-0 test">
			<div class="at primary-font-0">
				<span class="material-symbols-outlined"> palette </span> Palette
			</div>
			<div class="hece">
				{#each [0, 10, 20, 30, 40, 50, 60, 70, 80, 90, 100] as codes}
					<div class={`primary-${codes} primary-font-${codes} hehe`}>
						{codes}
					</div>
				{/each}
			</div>
		</div>
	</div>

	<Card header="Phasellus fermentum semper" kind="neutral">
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
	</Card>

	<Card header="Mauris hendrerit ultricies" kind="neutral">
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
	</Card>
	<Card header="Libero vel vulputate">
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
	</Card>
</div>

<div class="neutral-80 neutral-font-80">i have spoken</div>

<style lang="scss">
	.attr {
		display: flex;
		background: var(--neutral-80);
		border-radius: 8px;
		flex-direction: column;
		overflow: hidden;
	}
	.at {
		display: flex;
		align-items: center;
		gap: 0.5rem;
		padding-left: 1rem;
		font-size: 0.75rem;
	}
	.test {
		margin: 0;
		display: flex;
		overflow: hidden;
		justify-content: space-between;
		align-items: center;
	}

	.hehe {
		width: 2.5rem;
		height: 2.5rem;
		font-size: 14px;
		display: flex;
		align-items: flex-start;
		justify-content: flex-end;
		padding: 0.5rem;
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

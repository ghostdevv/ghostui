<script lang="ts">
	import KitchenSink from './testing-pages/KitchenSink.svelte';
	import Pico from './testing-pages/Pico.svelte';

	const TESTING_PAGES = Object.freeze({
		KitchenSink,
		Pico,
	});

	type Option = keyof typeof TESTING_PAGES;

	const options = Object.keys(TESTING_PAGES) as Option[];

	let selected: Option = 'KitchenSink';
</script>

<header>
	{#each options as option}
		<button
			class="outline"
			class:active={selected == option}
			on:click={() => (selected = option)}
		>
			{option}
		</button>
	{/each}

	<hr />
</header>

{#if selected}
	<svelte:component this={TESTING_PAGES[selected]}></svelte:component>
{/if}

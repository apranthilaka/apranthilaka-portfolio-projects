<!-- <script lang="ts">
	import './layout.css';
	import favicon from '$lib/assets/favicon.svg';

	let { children } = $props();
</script>

<svelte:head><link rel="icon" href={favicon} /></svelte:head>
{@render children()} -->

<script lang="ts">
	import './layout.css';
	import favicon from '$lib/assets/favicon.svg';
	import { fade, fly } from 'svelte/transition';
	import { navigating } from '$app/state';

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>

{#key navigating.to?.url.pathname}
	<div in:fly={{ y: 0, duration: 400 }} out:fade={{ duration: 500 }}>
		{@render children()}
	</div>
{/key}

<script lang="ts">
	import Button from '$lib/components/Button.svelte';
	// import DisplayName from '$lib/components/DisplayName.svelte';
	// import RandomNumber from '$lib/components/RandomNumber.svelte';
	// import Counter from '$lib/components/Counter.svelte';

	import { Search, Baby, AlarmClock } from '@lucide/svelte';

	let html = '<p>Hello</p>';
</script>

<!-- {#snippet left()}
	<Search />
{/snippet} -->

<!-- <DisplayName /> -->
<!-- <RandomNumber /> -->
<!-- <Counter /> -->
<div class="wrapper">
	{@html html}
	<Button
		size="lg"
		shadow
		disabled
		aria-label="up"
		--buttonBgColor="yellow"
		--buttonTextColor="green"
		onc
	>
		{#snippet left(isHovered: boolean)}
			{#if isHovered}
				<Search />
			{:else}
				<AlarmClock />
			{/if}
		{/snippet}

		<!-- Need to find out why it's not working when  -->
		<!-- {#snippet children(isHovered: boolean)}
		Text {isHovered}
	{/snippet} -->

		Text
		{#snippet right()}
			<Baby />
		{/snippet}
	</Button>
</div>

<style>
	:global(body) {
		background-color: #222;
	}

	@keyframes --global-move {
	}

	.wrapper :global {
		/* button {
			background-color: blue !important;
		} */

		p {
			color: white;
		}
	}
</style>

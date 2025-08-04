<script lang="ts">
	import Button from '$lib/components/Button.svelte';
	// import DisplayName from '$lib/components/DisplayName.svelte';
	// import RandomNumber from '$lib/components/RandomNumber.svelte';
	// import Counter from '$lib/components/Counter.svelte';

	import { Search, Baby, AlarmClock } from '@lucide/svelte';

	let html = '<p>Hello</p>';
	let button: Button;

	$effect(() => {
		// console.log(button.getButton());
		button.getButton().focus();
		// button.focus();
	});
</script>

<!-- {#snippet left()}
	<Search />
{/snippet} -->

<!-- <DisplayName /> -->
<!-- <RandomNumber /> -->
<!-- <Counter /> -->
<div class="wrapper">
	{@html html}
	<div
		role="presentation"
		onclick={(e) => {
			console.log('event coming from div');
		}}
	>
		<Button
			bind:this={button}
			href={undefined}
			size="lg"
			shadow
			aria-label="up"
			--buttonBgColor="yellow"
			--buttonTextColor="green"
			onclick={(e) => {
				e.stopPropagation();
				console.log('event coming from button');
			}}
			leftHover={() => {
				console.log('left hovered');
			}}
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

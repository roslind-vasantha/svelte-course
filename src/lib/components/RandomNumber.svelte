<script lang="ts">
	import { onDestroy, onMount, tick, untrack } from 'svelte';

	let randomNumber = $state(Math.floor(Math.random() * 10));
	let doubleRandomNumber = $derived(randomNumber * 2);
	// let doubleRandomNumber = $state(0);
	let history: number[] = $state([untrack(() => randomNumber)]);
	let historyPTag: HTMLParagraphElement;

	// $effect(() => {
	// 	doubleRandomNumber = randomNumber * 2;
	// });

	// $effect(() => {
	// 	randomNumber;
	// 	untrack(() => {
	// 		history.push(randomNumber);
	// 	});
	// });

	onMount(() => {
		console.log('Component has mounted');

		return () => {
			console.log('Component has unmounted');
		};
	});

	onDestroy(() => {
		console.log('Component is destroyed');
	});

	$effect.pre(() => {
		// history.length;
		console.log('$effect.pre', history.length);
		console.log('$effect.pre', historyPTag?.innerText);
		tick().then(() => {
			console.log('After tick', historyPTag.innerHTML);
		});

		return () => {
			console.log('Pre effect cleanup');
		};
	});

	$effect(() => {
		// history.length;
		console.log('$effect', history.length);
		console.log('$effect', historyPTag.innerText);

		return () => {
			console.log('Effect cleanup');
		};
	});
</script>

<h2>The random number is {randomNumber}</h2>
<h2>Double random number is {doubleRandomNumber}</h2>
<p bind:this={historyPTag}>History: {history}</p>

<button
	onclick={() => {
		randomNumber = Math.floor(Math.random() * 10);
		history.push(randomNumber);
		console.log({ randomNumber, doubleRandomNumber });
	}}
>
	Generate
</button>

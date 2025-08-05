<script lang="ts">
	let array = $state([1, 2, 3, 4]);
	let objectsArray = $state([{ id: 1 }, { id: 2 }]);
	let object = $state({
		firstName: 'Ali',
		lastName: 'Afroze',
		address: {
			city: 'City',
			street: 'Street'
		}
	});

	// $effect(() => {
	// 	console.log(object);
	// });

	// $inspect(object).with(console.trace);

	$effect(() => {
		$inspect.trace();
		console.log(object.firstName);
		console.log(object.address.city);
	});
</script>

{@debug object, array}
<h1>{object.firstName}</h1>
<h2>{object.address.city}</h2>

<input bind:value={object.firstName} />
<input bind:value={object.address.city} />
<input bind:value={object.address.street} />
<p>{array}</p>
<button
	onclick={() => {
		// array.push(Math.round(Math.random() * 10));
		// array[0] = Math.round(Math.random() * 10);
		array[1] = Math.round(Math.random() * 10);
	}}>Add to array</button
>

<button
	onclick={() => {
		// console.log(object);
		console.log($state.snapshot(object));
	}}
>
	Log snapshot
</button>

<style>
	:global(body) {
		background-color: #222;
		color: #fff;
	}
</style>

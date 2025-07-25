<script lang="ts">
	let firstName = $state('Roslind');
	let lastName = $state('Vasantha');
	let userName = $state('roslind10');

	// let fullName = $derived(`${firstName} ${lastName}`);
	let fullName = $derived.by(() => {
		// userName = 'hhhh';
		console.log('Fullname derived');
		return `${firstName} ${lastName}`;
	});

	// let src = 'https://picsum.photos/id/237/200/300';
	let bio = 'Hello, <b>this</b> is me';

	$effect(() => {
		if (fullName || userName) {
			console.log('User has a username or fullname');
		}
	});
</script>

<!-- <img {src} alt="pup" /> -->
<!-- <input
	value={userName}
	oninput={(e) => {
		userName = e.currentTarget.value;
	}}
/> -->

<p>userName</p>
<input bind:value={userName} />
<p>firstName</p>
<input
	value={firstName}
	oninput={(e) => {
		firstName = e.currentTarget.value;
		// fullName = 'iiii';
		console.log(fullName, 'full');
	}}
/>
<p>lastName</p>
<input bind:value={lastName} />
<!-- <p>fullName</p> -->
<!-- <input bind:value={fullName} /> -->

<h1>Hello {userName || fullName}</h1>
<h1>Hello {fullName || userName}</h1>

<p>{@html bio}</p>

<style>
	h1 {
		color: red;
	}
</style>

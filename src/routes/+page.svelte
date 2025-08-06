<script lang="ts">
	import Notification from '$lib/components/Notification.svelte';
	import generateNotifications from '$lib/utils/generate-notifications';

	let notifications = $state(generateNotifications(3));

	// console.log(generateNotifications());
	// console.log(notifications);
	$inspect(notifications);
</script>

<ul>
	<!-- {#each notifications as notification, index}
		<li>
			{index}
			{notification.title}
		</li>
	{/each} -->

	<!-- {#each notifications as { title, body, date }}
		{@const dateObject = new Date(date)}
		<li>
			<h5>{title}</h5>
			<p>{body}</p>
			<time datetime={dateObject.toISOString()}>{dateObject.toLocaleDateString()}</time>
		</li>
	{:else}
		<p>no notifications</p>
	{/each} -->

	<!-- {#each notifications as notification, index} -->
	{#each notifications as notification, index (notification.id)}
		<li>
			<Notification
				{notification}
				onremove={(id) => {
					// alert(id);
					// notifications.splice(index, 1);

					// console.log(
					// 	$state.snapshot(notifications.filter((notification) => notification.id !== id))
					// );

					notifications = $state.snapshot(
						notifications.filter((notification) => notification.id !== id)
					);
				}}
			/>
		</li>
	{:else}
		<p>no notifications</p>
	{/each}
</ul>

<style>
	:global(body) {
		background-color: #222;
		color: #fff;
	}

	ul {
		list-style: none;
		padding: 10px;
		margin: 0;
		li {
			margin-bottom: 10px;
		}
	}
</style>

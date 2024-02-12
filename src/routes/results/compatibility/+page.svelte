<script>
	import { onMount } from 'svelte';

	// Value to display
	let value = 78;

	onMount(() => {
		value = JSON.parse(localStorage.getItem('result'))['compatibility'];
	});
</script>

<svelte:head>
	<title>Aircraft</title>
	<meta name="description" content="Validate how suitable you are for an idea in seconds." />
	<link rel="preconnect" href="https://fonts.googleapis.com" />
	<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
	<link
		href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600&family=Roboto+Mono&display=swap"
		rel="stylesheet"
	/>
	<script src="https://cdnjs.cloudflare.com/ajax/libs/parallax/3.1.0/parallax.min.js"></script>
</svelte:head>

<section class="centered" style="width: 580px;">
	<h3>Done! 🎉</h3>
	<h4>Here’s your suitability score:</h4>
	{value} out of 100
	<a href="/results/general" class="enabled">See Why</a>
</section>

<style>
	.enabled {
		background-color: #fff;
		color: #111;
		box-shadow: 0px 0px 2px 0px rgba(0, 0, 0, 0.25);
		pointer-events: all;
		border: 1px solid #ddd;
		cursor: pointer;
		text-align: center;
	}
	a {
		color: #fff;
		font-size: 16px;
		font-weight: 600;
		background-color: #ddd;
		text-align: center;
		border: none;
		border-radius: 8px;
		cursor: pointer;
		padding: 15px 24px;
		text-decoration: none;
		pointer-events: none;
		cursor: default;
	}
</style>

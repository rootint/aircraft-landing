<script>
	import { onMount } from 'svelte';

	// Value to display
	let audience = [];

	onMount(() => {
		let result = JSON.parse(localStorage.getItem('result'));
		audience = result['target_audience'];
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

<section class="centered">
	<h3>Target Audience</h3>
	<h4>Learn about who your ideal audience is</h4>
	{audience}
	<a href="/results/marketing" class="enabled">Next</a>
</section>

<style>
	.description {
		margin-top: 16px;
		margin-bottom: 16px;
		max-width: 500px;
		padding: 8px 16px;
		border-radius: 8px;
		border: 1px solid #ddd;
	}
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

	h3 {
		font-size: 20px;
		font-weight: 600;
		margin: 0px;
		margin-bottom: 24px;
	}

	h4 {
		font-size: 16px;
		font-weight: 500;
		color: #777;
		margin: 0;
		margin-bottom: 16px;
		line-height: 140%;
	}
	section.centered {
		/* background-color: aqua; */
		justify-content: center;
		display: flex;
		flex-direction: column;
		animation: fadeIn 0.7s ease;
		background-color: #fff;
		padding: 32px;
		border: 1px solid #ddd;
		box-shadow: 0px 0px 4px 0px rgba(0, 0, 0, 0.25);
		border-radius: 8px;
		max-width: 520px;
	}
</style>

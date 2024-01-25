<script>
	import { onMount } from 'svelte';

	let result = '';

	onMount(() => {
		result = localStorage.getItem('result');
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
	<h3>Great Job! You’ve made it this far.</h3>
	<h3>
		Below are the things you need to build this product and <br /> the team you need behind you.
	</h3>
	<p>
		{result}
	</p>
</section>

<style>
	h3 {
		font-size: 16px;
		font-weight: 500;
		margin-bottom: 12px;
		text-align: center;
	}
	section.centered {
		/* background-color: aqua; */
		justify-content: center;
		align-items: center;
		display: flex;
		flex-direction: column;
		animation: fadeIn 0.7s ease;
	}
</style>

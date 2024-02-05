<script>
	import { onMount } from 'svelte';
	import SvelteMarkdown from 'svelte-markdown';

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
	<h4>
		Below are the things you need to build this product and <br /> the team you need behind you.
	</h4>
	<div class="gradient-wrapper">
		<div class="result-container">
			<SvelteMarkdown source={result} />
		</div>
	</div>
</section>

<style>
	.gradient-wrapper {
		padding: 2px 2px;
		background: linear-gradient(
			to bottom right,
			#91de45,
			#45dea7,
			#454ade,
			#8347de,
			#de4545,
			#91de45,
			#45dea7,
			#454ade,
			#8347de,
			#de4545
		);
		background-size: 200% 200%;
		border-radius: 10px;
		margin-top: 16px;
		box-shadow: 0px 0px 2px 0px rgba(0, 0, 0, 0.25);
	}
	.result-container {
		background-color: #fff;
		padding: 16px 32px;
		border-radius: 8px;
	}
	h3 {
		font-size: 20px;
		font-weight: 500;
		margin-bottom: 12px;
		text-align: center;
	}
	h4 {
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
		max-width: 700px;
	}
</style>

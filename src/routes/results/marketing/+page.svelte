<script>
	import { ChevronLeft } from 'lucide-svelte';
	import { onMount } from 'svelte';

	// Value to display
	let marketing = [];
	// TODO: add concrete social media links, like linkedin and facebook or whatever
	onMount(() => {
		let result = JSON.parse(localStorage.getItem('result'));
		marketing = result['marketing'];
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
	<h3>Marketing</h3>
	<h4>Here are some marketing tips:</h4>
	{#each marketing as hint}
		<div class="summary">
			{hint}
		</div>
	{/each}
	<div class="button-row" style="margin-top: 8px;">
		<a href="/results/team" class="back-button"><ChevronLeft color="#111111" /></a>
		<a href="/results/audience" class="continue">Next</a>
	</div>
</section>

<style>
	.summary {
		margin-bottom: 16px;
		padding: 16px 16px;
		border-radius: 8px;
		border: 1px solid #ddd;
		line-height: 130%;
		font-size: 14px;
	}
	.continue {
		width: 100%;
		color: #111;
		font-size: 16px;
		font-weight: 600;
		text-align: center;
		border-radius: 8px;
		cursor: pointer;
		padding: 15px 24px;
		text-decoration: none;
		background-color: #fff;
		border: 1px solid #ddd;
		box-shadow: 0px 0px 2px 0px rgba(0, 0, 0, 0.25);
		pointer-events: all;
		cursor: pointer;
	}
</style>

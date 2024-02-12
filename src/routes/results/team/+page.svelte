<script>
	import { ChevronLeft, Hammer, PenTool, Wrench } from 'lucide-svelte';
	import { onMount } from 'svelte';

	// Value to display
	let team = [];

	onMount(() => {
		let result = JSON.parse(localStorage.getItem('result'));
		team = result['teammates'];
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
	<h3>Team</h3>
	<h4>Here’s the team you need to build the product:</h4>
	{#each team as teammate, index}
		<div class="summary">
			{#if index == 0}
				<Wrench size="17" color="#555" style="margin-right: 12px;" />
			{:else if index == 1}
				<Hammer size="17" color="#555" style="margin-right: 12px;" />
			{:else}
				<PenTool size="17" color="#555" style="margin-right: 12px;" />
			{/if}

			{teammate}
		</div>
	{/each}
	<div class="button-row">
		<a href="/results/general" class="back-button"><ChevronLeft color="#111111" /></a>
		<a href="/results/marketing" class="continue">Next</a>
	</div>
</section>

<style>
	.summary {
		margin-bottom: 24px;
		padding: 16px 16px;
		border-radius: 8px;
		border: 1px solid #ddd;
		line-height: 120%;
		width: 100%;
		font-weight: 500;
		display: flex;
		align-items: center;
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

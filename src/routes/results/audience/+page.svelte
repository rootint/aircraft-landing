<script>
	import { onMount } from 'svelte';
	import Modal from '../../../components/Modal.svelte';

	// Value to display
	// TODO: add more detail to the target audience, explaining why this audience is suitable
	let audience = [];

	onMount(() => {
		let result = JSON.parse(localStorage.getItem('result'));
		audience = result['target_audience'];
	});

	function handleSubmit() {}
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

<div style="display: flex; flex-direction: column; align-items: center;">
	<section class="centered">
		<h3>Target Audience</h3>
		<h4>Learn about who your ideal audience is</h4>
		<div class="summary">
			{audience}
		</div>
		<a href="/results/marketing" class="continue">Back</a>
	</section>
	<div style="height: 32px" />
	<Modal />
</div>

<style>
    section.centered {
        margin-bottom: 0px;
    }
	.summary {
		margin-bottom: 24px;
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

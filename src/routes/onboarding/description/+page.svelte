<script>
	import { onMount } from 'svelte';

	let description = '';
	let isButtonEnabled = false;

	onMount(() => {
		if (localStorage.getItem('description')) {
			description = localStorage.getItem('description');
            isButtonEnabled = true;
		}
	});

	function handleSubmit() {
		console.log(`Sent ${description}`);
		localStorage.setItem('description', description);
	}

	function checkButton() {
		isButtonEnabled = description.length != 0;
	}
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
	<h3>Step 1. Description</h3>
	<h4>
		Describe your project as much as you can. Make sure to include your target audience and key
		features.
	</h4>
	<textarea
		bind:value={description}
		on:input={checkButton}
		class="benefit-input"
		placeholder="An AI-powered learning assistant leveraging an LLM that offers personalized academic support to students, including homework solutions, study planning, and language learning, adapting to individual needs and learning styles."
	/>
	<a
		href="/onboarding/experience"
		on:click={handleSubmit}
		class={isButtonEnabled ? 'continue enabled' : 'continue'}>Continue</a
	>
</section>

<style>
	.continue.enabled {
		background-color: #111;
		box-shadow: 0px 0px 2px 0px rgba(0, 0, 0, 0.25);
		pointer-events: all;
		cursor: pointer;
		text-align: center;
	}
	.continue {
		width: 100%;
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
	.benefit-input {
		max-width: 520px;
		max-lines: 5;
		font-weight: 400;
		font-style: normal;
		font-size: 14px;
		background-color: #fff;
		color: #111;
		padding: 16px;
		border-radius: 8px;
		border: 1px solid #ddd;
		/* box-shadow: 0px 0px 2px 0px rgba(0, 0, 0, 0.25); */
		opacity: 1;
		resize: none;
		/* height: calc(16px * 3 + 24px); */
		height: 150px;
		overflow-y: auto;
		margin-bottom: 24px;
	}

	.benefit-input:focus {
		outline: none;
		border: solid #333 1px;
	}
	.benefit-input::placeholder {
		color: #aaa;
	}
</style>

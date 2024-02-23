<script>
	import { fade } from 'svelte/transition';
	import { Linkedin, ChevronRight, ChevronLeft } from 'lucide-svelte';

	// let visible = false;
	// let isButtonEnabled = true;
	// let experience = '';
	// let result = { summary: 'hi guys this is a summary' };

	let isLinkedInEnabled = false;
	let username = '';
	let experience = '';
	let isButtonEnabled = false;
	let visible = true;
	let result = null;
	let noLinkedin = false;
	let isError = false;
	let isLoading = false;

	function handleSubmit() {
		console.log(`Sent ${experience}`);
		if (experience != '') {
			localStorage.setItem('experience', experience);
		}
	}
	async function getLinkedIn() {
		isError = false;
		isLoading = true;
		const endpoint = 'https://api.llime.co/aircraft/parse-linkedin';

		const response = await fetch(endpoint, {
			method: 'POST',
			headers: {
				'Content-Type': 'application/json'
			},
			body: JSON.stringify({
				username: username
			})
		});
		if (!response.ok) {
			isError = true;
			isLoading = false;
			isLinkedInEnabled = false;
			return;
		}

		result = await response.json();
		console.log(result);
		localStorage.setItem('experience', JSON.stringify(result));
		visible = false;
		isButtonEnabled = true;
	}

	function changeMode() {
		noLinkedin = !noLinkedin;
	}

	function checkButton() {
		isButtonEnabled = experience.length != 0;
		isLinkedInEnabled = username.length != 0;
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
	<h3>Step 2. Experience</h3>
	<h4>
		Seamlessly personalize your experience by importing your work and education history from
		LinkedIn, or share it with us manually.
	</h4>
	<textarea
		bind:value={experience}
		on:input={checkButton}
		class="default-input"
		placeholder="I'm an AI developer specializing in NLP, passionate about using my skills to create educational tools that adapt to individual learning styles and simplify complex academic concepts."
	/>
	<div class="button-row">
		<a href="/onboarding/description" class="back-button"><ChevronLeft color="#111111" /></a>

		{#if visible}
			{#if isButtonEnabled}
				<a href="/onboarding/why" on:click={handleSubmit} class="continue">Continue</a>
			{:else}
				<button on:click={changeMode} disabled="true" class="linkedin-switch-btn">Continue</button>
			{/if}
		{:else}
			<a href="/onboarding/why" on:click={handleSubmit} class="continue">Continue</a>
		{/if}
	</div>
</section>

<style>
	.summary {
		margin-bottom: 24px;
		padding: 4px 16px;
		border-radius: 8px;
		border: 1px solid #ddd;
	}

	.email-row {
		display: flex;
		width: 100%;
		margin-bottom: 24px;
	}
	.hide-mobile {
	}
	span {
		font-weight: 400;
		font-style: normal;
		font-size: 1rem;
		color: #555;
		margin-left: 12px;
	}
	.email-container {
		background-color: #fff;
		color: #111;
		padding: 0px 16px;
		border-radius: 8px;
		border: none;
		border: 1px solid #ddd;
		opacity: 1;
		display: flex;
		align-items: center;
	}
	.email-container:focus {
		outline: none;
		border: 1px solid #111;
	}

	.email-input {
		border: none;
		outline: none;
		width: 100%;
		font-weight: 500;
		font-style: normal;
		font-size: 1rem;
		padding: none;
	}

	.linkedin-submit-btn {
		color: #fff;
		background-color: #111;
		box-shadow: 0px 0px 2px 0px rgba(0, 0, 0, 0.25);
		pointer-events: all;
		cursor: pointer;
		border: none;
		display: block;
		border-radius: 8px;
		font-size: 16px;
		font-weight: 500;
		padding: 0 12px;
	}

	.linkedin-submit-btn.disabled {
		box-shadow: none;
		color: #fff;
		background-color: #ddd;
		pointer-events: none;
		cursor: default;
	}

	.linkedin-switch-btn {
		color: #fff;
		background-color: #ddd;
		pointer-events: none;
		/* cursor: pointer; */
		border: 1px solid #ddd;
		display: block;
		border-radius: 8px;
		width: 100%;
		font-size: 16px;
		font-weight: 500;
	}
	.continue {
		width: 100%;
		text-align: center;
		color: #fff;
		font-size: 16px;
		font-weight: 500;
		background-color: #111;
		border: none;
		border-radius: 8px;
		cursor: pointer;
		padding: 15px 24px;
		text-decoration: none;
		box-shadow: 0px 0px 2px 0px rgba(0, 0, 0, 0.25);
	}
	@media (max-width: 800px) {
		.email-container {
			width: 100%;
			font-size: 1rem;
			padding: 12px;
			height: unset;
		}
	}
	@media (max-width: 800px) {
		.hide-mobile {
			display: none;
		}
		.email-row {
			display: flex;
			flex-direction: column;
			width: 100%;
			margin-bottom: 24px;
		}
		.email-container {
			background-color: #fff;
			color: #111;
			border-radius: 8px;
			border: none;
			border: 1px solid #ddd;
			opacity: 1;
			display: flex;
			align-items: center;
			margin-bottom: 16px;
		}
		.linkedin-submit-btn {
			color: #fff;
			background-color: #111;
			box-shadow: 0px 0px 2px 0px rgba(0, 0, 0, 0.25);
			pointer-events: all;
			cursor: pointer;
			border: none;
			display: block;
			border-radius: 8px;
			font-size: 16px;
			font-weight: 500;
			padding: 12px;
		}
		.linkedin-submit-btn.disabled {
			box-shadow: none;
			color: #fff;
			background-color: #ddd;
			pointer-events: none;
			cursor: default;
			padding: 12px 12px;
		}
	}
</style>

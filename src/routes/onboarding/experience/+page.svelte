<script>
	import { fade } from 'svelte/transition';
	import { Linkedin, ChevronRight } from 'lucide-svelte';

	let experience = '';
	let isButtonEnabled = false;
	let isLinkedInEnabled = false;
	let username = '';
	let visible = true;
	let noLinkedin = false;
	let isError = false;
	let isLoading = false;
	let result = null;

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
			// throw new Error(`Error: ${response.status}`);
			isError = true;
			isLoading = false;
			isLinkedInEnabled = false;
			return;
		}

		result = await response.json();
		console.log(result);
		localStorage.setItem('experience', JSON.stringify(result));
		// return data['message'];
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

	{#if !noLinkedin}
		{#if visible}
			<div class="email-row">
				<div class="email-container">
					<Linkedin size="48" color="#AAAAAA" />
					<span>https://linkedin.com/in/</span>
					<input
						bind:value={username}
						on:input={checkButton}
						class="email-input"
						placeholder="username"
					/>
				</div>

				<div style="width: 16px" />
				<button
					on:click={getLinkedIn}
					class={isLoading ? 'loading' : isLinkedInEnabled ? 'enabled' : ''}
					><ChevronRight /></button
				>
			</div>
		{/if}
		{#if isError}
			<p style="color: red; margin: 0; margin-bottom: 16px;">Your username is incorrect.</p>
		{/if}
		{#if !visible}
			<div class="description">
				<p style="font-size: 14px;">
					Summary: {result['summary']}
				</p>
			</div>
		{/if}
	{:else}
		<textarea
			bind:value={experience}
			on:input={checkButton}
			class="benefit-input"
			placeholder="An AI-powered learning assistant leveraging an LLM that offers personalized academic support to students, including homework solutions, study planning, and language learning, adapting to individual needs and learning styles."
		/>
	{/if}
	<!-- <div style="display: flex">
		<a href="/onboarding/description" on:click={handleSubmit} class="enabled"><ChevronLeft /></a>
		<div style="width: 16px" />
		
	</div> -->
	{#if visible}
		{#if isButtonEnabled}
			<a href="/onboarding/why" on:click={handleSubmit} class="enabled">Continue</a>
		{:else}
			<button on:click={changeMode} class="enabled-big"
				>I {!noLinkedin ? "don't" : ''} have a LinkedIn account</button
			>
		{/if}
	{:else}
		<a href="/onboarding/why" on:click={handleSubmit} class="enabled">Continue</a>
	{/if}
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
	.loading {
		pointer-events: none;
	}
	.removable {
		display: flex;
		flex-direction: column;
		align-items: center;
	}
	.email-row {
		display: flex;
		width: 100%;
		margin-bottom: 24px;
	}
	span {
		font-weight: 400;
		font-style: normal;
		font-size: 1rem;
		color: #555;
		margin-left: 12px;
	}
	.email-container {
		/* width: 20rem;z */
		background-color: #fff;
		color: #111;
		padding: 0px 16px;
		border-radius: 8px;
		border: none;
		border: 1px solid #ddd;
		/* box-shadow: 0px 0px 2px 0px rgba(0, 0, 0, 0.25); */
		opacity: 1;
		display: flex;
		align-items: center;
	}
	@media (max-width: 800px) {
		.email-container {
			width: 100%;
			font-size: 1rem;
			padding: 16px;
			height: unset;
		}
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

	button.enabled {
		background-color: #111;
		box-shadow: 0px 0px 2px 0px rgba(0, 0, 0, 0.25);
		pointer-events: all;
		cursor: pointer;
	}

	button.enabled-big {
		color: #111;
		background-color: #fff;
		box-shadow: 0px 0px 2px 0px rgba(0, 0, 0, 0.25);
		pointer-events: all;
		cursor: pointer;
		border: 1px solid #ddd;
		display: block;
	}

	a.enabled {
		background-color: #fff;
		box-shadow: 0px 0px 2px 0px rgba(0, 0, 0, 0.25);
		border: 1px solid #ddd;
		pointer-events: all;
		cursor: pointer;
	}
	a {
		text-align: center;
		color: #111;
		font-size: 16px;
		font-weight: 500;
		background-color: #fff;
		border: none;
		border-radius: 8px;
		cursor: pointer;
		padding: 15px 24px;
		text-decoration: none;
		pointer-events: none;
		cursor: default;
	}

	button {
		display: flex;
		align-items: center;
		color: #fff;
		font-size: 16px;
		font-weight: 500;
		background-color: #ddd;
		border: none;
		border-radius: 8px;
		cursor: pointer;
		padding: 16px 16px;
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

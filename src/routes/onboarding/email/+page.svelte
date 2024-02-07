<script>
	import { goto } from '$app/navigation';

	let email = '';
	let submitted = false;
	$: isEmailValid = /^\w+([.-]?\w+)*@\w+([.-]?\w+)*(\.\w{2,3})+$/.test(email);

	async function handleSubmit() {
		console.log(`Submitting ${email}`);
		submitted = true;
		const endpoint = 'http://localhost:1337/send-receive-message';

		const response = await fetch(endpoint, {
			method: 'POST',
			headers: {
				'Content-Type': 'application/json'
			},
			body: JSON.stringify({
				description: localStorage.getItem('description'),
				experience: localStorage.getItem('experience'),
                why: localStorage.getItem('why'),
                idea: localStorage.getItem('idea'),
                acute: localStorage.getItem('acute')
			})
		});
		if (!response.ok) {
			throw new Error(`Error: ${response.status}`);
		}

		const data = await response.json();
		console.log(data);
		localStorage.setItem('result', data);
		await goto('/results/compatibility/');
		// return data['message'];
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
	<h3>Last Step. Email Address</h3>
	<h4>We will send the results to your email. No spam, we promise.</h4>
	<input type="email" bind:value={email} class="email-input" placeholder="example@email.com" />

	{#if submitted}
		<p>Thank you! Your answer is loading.</p>
	{:else}
		<button on:click={handleSubmit} disabled={!isEmailValid}>See Results</button>
	{/if}
</section>

<style>
	p {
		font-size: 14px;
		font-weight: 400;
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
	.email-input {
		margin-top: 6px;
		font-weight: 400;
		font-style: normal;
		font-size: 1rem;
		background-color: #fff;
		color: #111;
		padding: 16px;
		border-radius: 8px;
		border: none;
		border: 1px solid #ddd;
		box-shadow: 0px 0px 2px 0px rgba(0, 0, 0, 0.25);
		opacity: 1;
		margin-bottom: 24px;
	}
	@media (max-width: 800px) {
		.email-input {
			width: 100%;
			font-size: 1rem;
			padding: 16px;
			height: unset;
		}
	}

	.email-input:focus {
		outline: none;
		border: 1px solid #111;
	}

	.email-input::placeholder {
		font-weight: 400;
		color: #aaa;
	}
	section.centered {
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
	button {
		align-items: center;
		color: #fff;
		font-size: 16px;
		font-weight: 500;
		border: none;
		border-radius: 8px;
		cursor: pointer;
		padding: 15px 24px;
		text-decoration: none;
		background-color: #111;
		box-shadow: 0 0 2px #111;
		pointer-events: all;
		cursor: pointer;
	}
	button:disabled {
		box-shadow: none;
		background-color: #ddd;
		border: none;
		border-radius: 8px;
		cursor: pointer;
		padding: 15px 24px;
		text-decoration: none;
		pointer-events: none;
		cursor: default;
	}
</style>

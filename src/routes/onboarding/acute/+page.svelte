<script>
	import { ChevronLeft } from 'lucide-svelte';

	let selectedOption = 'I strongly agree that this is a critical problem';

	function handleSubmit() {
		localStorage.setItem('acute', `How acute is the problem? Answer: ${selectedOption}`);
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

<section class="centered" style="width: 580px;">
	<h3>Step 5. How acute is the problem?</h3>
	<h4>Choose one option below</h4>
	<form>
		<label>
			<input
				type="radio"
				bind:group={selectedOption}
				value="I strongly agree that this is a critical problem"
			/>
			I strongly agree that this is a critical problem
		</label>

		<label>
			<input
				type="radio"
				bind:group={selectedOption}
				value="I believe this is a somewhat acute problem"
			/>
			I believe this is a somewhat acute problem
		</label>

		<label>
			<input type="radio" bind:group={selectedOption} value="In my view, this is a minor problem" />
			In my view, this is a minor problem
		</label>
	</form>
	<div class="button-row">
		<a href="/onboarding/idea" class="back-button"><ChevronLeft color="#111111" /></a>
		<a href="/onboarding/email" on:click={handleSubmit} class="continue enabled">Confirm</a>
	</div>
</section>

<style>
	input[type='radio'] {
		accent-color: #111;
		margin-right: 8px;
	}
	label {
		width: 100%;
		border: 1px solid #ddd;
		border-radius: 8px;
		padding: 16px;
		margin-bottom: 16px;
	}
	form {
		display: flex;
		flex-direction: column;
		margin: 0;
		margin-bottom: 8px;
	}
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
</style>

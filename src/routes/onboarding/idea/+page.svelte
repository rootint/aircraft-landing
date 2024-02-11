<script>
	import { ChevronLeft } from 'lucide-svelte';

	let selectedOption = 'no';

	function handleSubmit() {
		localStorage.setItem(
			'idea',
			`Is this an idea you’d want to work on for years? Answer: ${selectedOption}`
		);
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
	<h3>Step 4. Is this an idea you’d want to work on for years?</h3>
	<h4>Choose one option below</h4>
	<form>
		<label>
			<input type="radio" bind:group={selectedOption} value="yes" />
			Yes
		</label>

		<label>
			<input type="radio" bind:group={selectedOption} value="no" />
			No
		</label>

		<label>
			<input type="radio" bind:group={selectedOption} value="maybe" />
			Maybe
		</label>
	</form>
	<div class="button-row">
		<a href="/onboarding/why" class="back-button"><ChevronLeft color="#111111" /></a>
		<a href="/onboarding/acute" on:click={handleSubmit} class="continue enabled">Confirm</a>
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

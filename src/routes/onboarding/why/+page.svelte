<script>
	import { ChevronLeft } from 'lucide-svelte';
	import { onMount } from 'svelte';

	let why = '';
	let isButtonEnabled = false;

	onMount(() => {
		if (localStorage.getItem('why')) {
			why = localStorage.getItem('why');
			isButtonEnabled = true;
		}
	});

	function handleSubmit() {
		console.log(`Sent ${why}`);
		if (why != '') {
			localStorage.setItem('why', why);
		}
	}

	function checkButton() {
		isButtonEnabled = why.length != 0;
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
	<h3>Step 3. Why are you the right person to build this?</h3>
	<h4>
		What unique experiences do you possess that uniquely positions you to bring this vision to life?
	</h4>
	<textarea
		bind:value={why}
		on:input={checkButton}
		class="default-input"
		placeholder="As a seasoned software engineer with a strong portfolio in developing scalable e-commerce platforms, my expertise in AI and machine learning algorithms positions me uniquely to revolutionize how online shopping interfaces can be made more intuitive and personalized."
	/>
	<div class="button-row">
		<a href="/onboarding/experience" class="back-button"><ChevronLeft color="#111111" /></a>
		<a
			href="/onboarding/idea"
			on:click={handleSubmit}
			class={isButtonEnabled ? 'continue enabled' : 'continue'}>Continue</a
		>
	</div>
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
</style>

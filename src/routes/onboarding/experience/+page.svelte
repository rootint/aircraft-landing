<script>
	let experience = '';
	let isButtonEnabled = false;

	function handleSubmit() {
		console.log(`Sent ${experience}`);
        localStorage.setItem('experience', experience);
	}
	function checkButton() {
		isButtonEnabled = experience.length != 0;
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
	<h3>We want to know more about your experience and what you do.</h3>
	<textarea
		bind:value={experience}
        on:input={checkButton}
		class="benefit-input"
		placeholder="I'm an AI developer specializing in NLP, passionate about using my skills to create educational tools that adapt to individual learning styles and simplify complex academic concepts."
	/>
	<a href="/onboarding/email" on:click={handleSubmit} class={isButtonEnabled ? 'enabled' : ''}
		>Next</a
	>
</section>

<style>
	.enabled {
		background-color: #111;
		box-shadow: 0 0 2px #111;
		pointer-events: all;
		cursor: pointer;
	}
	a {
		display: flex;
		align-items: center;
		color: #fff;
		font-size: 16px;
		font-weight: 500;
		background-color: #ddd;
		border: none;
		border-radius: 8px;
		cursor: pointer;
		padding: 15px 24px;
		text-decoration: none;
		pointer-events: none;
		cursor: default;
	}

	h3 {
		font-size: 16px;
		font-weight: 500;
		margin-bottom: 24px;
	}
	.benefit-input {
		width: 500px;
		max-lines: 3;
		font-weight: 400;
		font-style: normal;
		font-size: 16px;
		background-color: #fff;
		color: #111;
		padding: 12px;
		border-radius: 8px;
		border: 1px solid #ddd;
		box-shadow: 0px 0px 2px 0px rgba(0, 0, 0, 0.25);
		opacity: 1;
		resize: none;
		/* height: calc(16px * 3 + 24px); */
		height: 100px;
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
		align-items: center;
		display: flex;
		flex-direction: column;
        animation: fadeIn 0.7s ease;
	}
</style>

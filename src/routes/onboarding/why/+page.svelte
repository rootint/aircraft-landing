<script>
	let why = '';
	let isButtonEnabled = false;

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
		Highlight the skills and experiences that make you the perfect fit for bringing this vision to
		life.
	</h4>
	<textarea
		bind:value={why}
		on:input={checkButton}
		class="benefit-input"
		placeholder="As a seasoned software engineer with a strong portfolio in developing scalable e-commerce platforms, my expertise in AI and machine learning algorithms positions me uniquely to revolutionize how online shopping interfaces can be made more intuitive and personalized."
	/>
	<!-- <div style="display: flex;"> -->
	<!-- <a href="/onboarding/experience" on:click={handleSubmit} class="back"><ChevronLeft /></a> -->
	<a href="/onboarding/idea" on:click={handleSubmit} class={isButtonEnabled ? 'enabled' : ''}
		>Continue</a
	>
	<!-- </div> -->
</section>

<style>
	a.back {
		font-size: 16px;
		font-weight: 600;
		text-align: center;
		border: none;
		border-radius: 8px;
		cursor: pointer;
		text-decoration: none;
		background-color: #fff;
		box-shadow: 0px 0px 4px 0px rgba(0, 0, 0, 0.25);
		pointer-events: all;
		cursor: pointer;
		text-align: center;
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
	h3 {
		font-size: 20px;
		font-weight: 600;
		margin: 0px;
		margin-bottom: 24px;
		line-height: 140%;
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
	.enabled {
		background-color: #111;
		box-shadow: 0 0 2px #111;
		pointer-events: all;
		cursor: pointer;
		text-align: center;
	}
	a {
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

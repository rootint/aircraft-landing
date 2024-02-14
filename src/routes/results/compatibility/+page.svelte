<script>
	import { onMount } from 'svelte';

	// Value to display
	let value = 78;

	onMount(() => {
		value = JSON.parse(localStorage.getItem('result'))['compatibility'];
	});
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
	<h3>Done! 🎉</h3>
	<h4>Here’s your suitability score:</h4>
	<div class="value">
		{value}
		<span class="out-of">out of 100</span>
	</div>

	<a href="/results/general" class="enabled">See Why</a>
</section>

<style>
	.ring {
		position: relative;
		/* --pointerleft: 11%;
		--pointertop: 11%;
		--pointerdeg: -45deg; */
		width: 100%;
		aspect-ratio: 1;
		/* background-color: #eee; */
		border: #ddd 1px solid;
		background-image: #eee;
		/* background-image: radial-gradient(red 0, red 50%, transparent 50%, transparent 100%),
			radial-gradient(green 0, green 50%, transparent 50%, transparent 100%),
			radial-gradient(white 0, white 60%, transparent 60%),
			conic-gradient(orange 0, green 130deg, white 130deg, white 230deg, red 230deg, orange 360deg); */
		/* background-size: 11% 11%, 11% 11%, 100% 100%, 100% 100%; */
		background-repeat: no-repeat;
		/* background-position: 9.2% 82.3%, 90.8% 82.3%, center center, center center; */
		border-radius: 50%;
		border-style: none;
	}
	/* .ring {
		position: relative;
		--pointerleft: 11%;
		--pointertop: 11%;
		--pointerdeg: -45deg;
		width: 50vmin;
		height: 50vmin;
		background-image: radial-gradient(red 0, red 50%, transparent 50%, transparent 100%),
			radial-gradient(green 0, green 50%, transparent 50%, transparent 100%),
			radial-gradient(white 0, white 60%, transparent 60%),
			conic-gradient(orange 0, green 130deg, white 130deg, white 230deg, red 230deg, orange 360deg);
		background-size: 11% 11%, 11% 11%, 100% 100%, 100% 100%;
		background-repeat: no-repeat;
		background-position: 9.2% 82.3%, 90.8% 82.3%, center center, center center;
		border-radius: 50%;
		border-style: none;
	} */

	/* .ring::after {
		position: absolute;
		content: '';
		width: 5%;
		height: 15%;
		left: var(--pointerleft);
		top: var(--pointertop);
		transform: rotate(var(--pointerdeg));
		border-style: solid;
		border-width: 0.5vmin;
		border-radius: 2vmin;
		background-color: white;
	} */

	.speed {
		display: inline-block;
		position: absolute;
		top: 50%;
		left: 50%;
		transform: translateX(-50%) translateY(-50%);
		text-align: center;
	}

	.value {
		font-size: 64px;
		font-weight: 600;
		margin: 0;
		padding: 0;
		color: #111;
	}
	.out-of {
		font-size: 20px;
		font-weight: 400;
		color: #999;
		margin: 0;
		padding: 0;
	}
	.enabled {
		background-color: #fff;
		color: #111;
		box-shadow: 0px 0px 2px 0px rgba(0, 0, 0, 0.25);
		pointer-events: all;
		border: 1px solid #ddd;
		cursor: pointer;
		text-align: center;
	}
	a {
		margin-top: 16px;
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

<script>
	import { onMount } from 'svelte';

	// Value to display
	let value = 78;
	let max = 100;

	// SVG drawing parameters
	const width = 200;
	const height = 120;
	const strokeWidth = 10;
	const radius = Math.min(width, height) / 2 - strokeWidth;
	const circumference = 2 * Math.PI * radius;
	const startAngle = -Math.PI / 2; // -90 degrees
	const endAngle = Math.PI / 2; // 90 degrees

	onMount(() => {
		value = JSON.parse(localStorage.getItem('result'))['compatibility'];
	});

	// Function to calculate the arc path
	function describeArc(x, y, radius, startAngle, endAngle) {
		const start = polarToCartesian(x, y, radius, endAngle);
		const end = polarToCartesian(x, y, radius, startAngle);

		const largeArcFlag = endAngle - startAngle <= Math.PI ? '0' : '1';

		return ['M', start.x, start.y, 'A', radius, radius, 0, largeArcFlag, 0, end.x, end.y].join(' ');
	}

	function polarToCartesian(centerX, centerY, radius, angleInRadians) {
		return {
			x: centerX + radius * Math.cos(angleInRadians),
			y: centerY + radius * Math.sin(angleInRadians)
		};
	}

	// Calculate the filled arc proportion based on the value
	const filledArcAngle = startAngle + (value / max) * (endAngle - startAngle);
	const filledArc = describeArc(width / 2, height, radius, startAngle, filledArcAngle);
	const backgroundArc = describeArc(width / 2, height, radius, startAngle, endAngle);
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
	<h3>Done! 🎉</h3>
	<h4>Here’s your suitability score:</h4>
	<svg {width} {height}>
		<path d={backgroundArc} fill="none" stroke="#ddd" stroke-width={strokeWidth} />
		<path d={filledArc} fill="none" stroke="url(#gradient)" stroke-width={strokeWidth} />
		<defs>
			<linearGradient id="gradient" x1="0%" y1="0%" x2="100%" y2="0%">
				<stop offset="0%" style="stop-color:#ff0000;stop-opacity:1" />
				<stop offset="100%" style="stop-color:#00ff00;stop-opacity:1" />
			</linearGradient>
		</defs>
		<text
			x="50%"
			y="50%"
			fill="black"
			text-anchor="middle"
			alignment-baseline="central"
			font-size="20px"
		>
			{value}
		</text>
		<text
			x="50%"
			y="60%"
			fill="black"
			text-anchor="middle"
			alignment-baseline="central"
			font-size="10px"
		>
			out of {max}
		</text>
	</svg>
	<a href="/results/general" class="enabled">See Why</a>
</section>

<style>
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

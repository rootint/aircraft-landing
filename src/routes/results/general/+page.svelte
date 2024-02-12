<script>
	import { ChevronLeft } from 'lucide-svelte';
	import { onMount } from 'svelte';

	// Value to display
	let summary = '';
	let skills = [];

	onMount(() => {
		let result = JSON.parse(localStorage.getItem('result'));
		summary = result['summary'];
		skills = result['skills'];
		console.log(skills);
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

<section class="centered">
	<h3>You are a match!</h3>
	<h4>Here’s why we think you are suitable for the project:</h4>
	<div class="skills-container">
		<div class="skills-name-column">
			{#each skills as skill}
				<p class="row-title">{skill['name']}</p>
			{/each}
		</div>
		<div class="bar-and-rating">
			{#each skills as skill}
				<div class="rating-row">
					<div class="progress-container">
						<div
							class="progress-bar {skill['rating'] > 5 ? 'green' : 'orange'}"
							style="width: {(skill['rating'] / 10) * 100}%;"
						/>
					</div>
					<p class="rating">
						<span style="font-size: 16px; font-weight: 600; color: #111;">{skill['rating']}</span
						>/10
					</p>
				</div>
			{/each}
		</div>
	</div>
	<div class="summary">
		<p style="font-size: 14px; margin: 8px 0px; font-weight: 500;">
			{summary}
		</p>
	</div>
	<div class="button-row">
		<a href="/results/compatibility" class="back-button"><ChevronLeft color="#111111" /></a>
		<a href="/results/team" class="continue">Next</a>
	</div>
</section>

<style>
    h4 {
        margin-bottom: 0px;
    }
	.rating-row {
		display: flex;
		align-items: center;
	}
	.bar-and-rating {
		display: flex;
		flex-direction: column;
		justify-content: center;
		width: 100%;
	}
	.green {
		background-color: #45dea7;
	}

	.orange {
		background-color: #deaa45;
	}

	.progress-bar {
		height: 12px;
		border-radius: 8px;
		width: 0%;
		text-align: right;
		padding-right: 10px;
		line-height: 12px;
		color: white;
		transition: width 0.5s ease-in-out;
	}
	.progress-container {
		width: 100%;
		background-color: #eee;
		border: 1px solid #ddd;
		border-radius: 8px;
		margin: 0 16px;
		height: 14px;
	}
	.rating {
		font-size: 12px;
		color: #999;
	}
	.skills-container {
		display: flex;
		align-items: center;
        margin-bottom: 8px;
	}
	.row-title {
		font-weight: 500;
		margin: 24px 0;
	}
	.summary {
		margin-bottom: 24px;
		padding: 4px 16px;
		border-radius: 8px;
		border: 1px solid #ddd;
		line-height: 120%;
	}
	.continue {
		width: 100%;
		color: #111;
		font-size: 16px;
		font-weight: 600;
		text-align: center;
		border-radius: 8px;
		cursor: pointer;
		padding: 15px 24px;
		text-decoration: none;
		background-color: #fff;
		border: 1px solid #ddd;
		box-shadow: 0px 0px 2px 0px rgba(0, 0, 0, 0.25);
		pointer-events: all;
		cursor: pointer;
	}
</style>

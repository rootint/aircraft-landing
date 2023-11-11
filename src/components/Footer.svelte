<script>
	import aircraft from '$lib/assets/aircraft.svg';

	let email = 'tioluwani@llime.co';
	let emailCopied = false;

	async function copyEmail() {
		try {
			await navigator.clipboard.writeText(email);
			console.log('Email copied to clipboard');
			emailCopied = true;
			// Optionally, show some user feedback that the email has been copied.
		} catch (err) {
			console.error('Failed to copy email', err);
			// Optionally, show some user feedback about the failure.
		}
	}
</script>

<div class="email-container-mobile">
	<p class="monospace-background" on:click={copyEmail}>
		{emailCopied ? 'Email Copied!' : 'Questions? tioluwani@llime.co'}
	</p>
</div>
<footer>
	<p>2023, Aircraft</p>
	<div class="email-container">
		<p class="monospace-background" on:click={copyEmail}>
			{emailCopied ? 'Email Copied!' : 'Questions? tioluwani@llime.co'}
		</p>
	</div>
	<div style="display: flex;">
		<p>Built using</p>
		<img src={aircraft} width="20" height="19" alt="Aircraft Logo" style="margin-left: 12px;" />
	</div>
</footer>

<style>
	footer {
		padding-bottom: 0px;
		display: flex;
		justify-content: space-between;
	}
	@media (max-width: 800px) and (max-height: 800px) {
		footer {
			margin-top: 16px;
			/* padding-bottom: 24px; */
			display: flex;
			/* flex-de */
			justify-content: space-between;
			align-items: end;
		}
	}
	p {
		font-weight: 500;
		margin: 0;
	}
	.email-container {
		/* position: absolute;
		height: 100%;
		width: 100vw; */
		/* top: 0;
		left: 0; */
		overflow: hidden;
		padding: 0;
		margin: 0;
		z-index: 1;
		display: flex;
		justify-content: center;
		cursor: pointer;
	}

	@media (max-width: 800px) {
		.email-container {
			display: none;
			width: 0;
		}
	}

	.email-container-mobile {
		display: none;
	}

	@media (max-width: 800px) {
		.email-container-mobile {
			/* position: absolute;
		height: 100%;
		width: 100vw; */
			/* top: 0;
		left: 0; */
			overflow: hidden;
			padding: 0;
			margin: 0;
			margin-top: 16px;
            margin-bottom: 16px;
			z-index: 1;
			display: flex;
			justify-content: center;
			cursor: pointer;
		}
	}

	p.monospace-background {
		font-family: 'Roboto Mono', monospace;
		margin: 0;
		color: #999;
		font-size: 16px;
		padding: 0;
	}

	p.monospace-background:hover {
		color: #777;
	}
</style>

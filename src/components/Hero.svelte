<script>
	let email = '';

	function validateText() {}

	function handleSubmit() {}
</script>

<section class="centered">
	<p>Loved by 100+ customers</p>
	<h1>Easiest landing page<br /> builder ever</h1>
	<h2>
		Create and share your landing page in 3 minutes.<br /> Boost visitor conversion and win more customers
		using AI.
	</h2>
	<div class="row">
		<input
			type="email"
			bind:value={email}
			on:input={validateText}
			class="email-input"
			placeholder="A startup that creates tailored AI models"
		/>
		<div style="width: 32px" />
		<div style="button-column">
			<div class="gradient-wrapper">
				<div class="another-wrapper">
					<button on:click={handleSubmit}>Build Now</button>
				</div>
			</div>
			<p class="monospace">It’s free. No login or<br />credit card required.</p>
		</div>
	</div>
</section>

<style>
	p.monospace {
		font-family: 'Roboto Mono', monospace;
		font-size: 16px;
		color: #888;
		margin-top: 8px;
		transition: color ease 0.2s;
	}

	.gradient-wrapper {
		padding: 2px 2px;
		background: linear-gradient(
			to bottom right,
			#91de45,
			#45dea7,
			#454ade,
			#8347de,
			#de4545,
			#91de45,
			#45dea7,
			#454ade,
			#8347de,
			#de4545
		);
		background-size: 200% 200%;
		border-radius: 12px;
	}

	.gradient-wrapper:hover {
		background: linear-gradient(
			to bottom right,
			#91de45,
			#45dea7,
			#454ade,
			#8347de,
			#de4545,
			#91de45,
			#45dea7,
			#454ade,
			#8347de,
			#de4545
		);
		background-size: 200% 200%;
		-webkit-animation: Animation 4s linear infinite;
		-moz-animation: Animation 4s linear infinite;
		animation: Animation 4s linear infinite;
	}

	@-webkit-keyframes Animation {
		0% {
			background-position: 10% 0%;
		}
		50% {
			background-position: 91% 100%;
		}
		100% {
			background-position: 10% 0%;
		}
	}
	@-moz-keyframes Animation {
		0% {
			background-position: 10% 0%;
		}
		50% {
			background-position: 91% 100%;
		}
		100% {
			background-position: 10% 0%;
		}
	}
	@keyframes Animation {
		0% {
			background-position: 10% 0%;
		}
		50% {
			background-position: 91% 100%;
		}
		100% {
			background-position: 10% 0%;
		}
	}

	.another-wrapper {
		background-color: #fff;
		border-radius: 10px;
		height: 100%;
		padding: 4px;
	}

	button {
		padding: 1.25rem 4rem;
		background: var(--text);
		font-weight: 500;
		font-size: 1.25rem;
		color: #fff;
		border: none;
		border-radius: 8px;
		/* margin-left: 10px; */
		cursor: pointer;
	}

	.email-input {
		margin-top: 6px;
		width: 30rem;
		height: 64px;
		font-weight: 400;
		font-style: normal;
		font-size: 1.25rem;
        background-color: #fff;
		color: #111;
		padding: 16px;
		border-radius: 8px;
		border: none;
		border: 1px solid #aaa;
        box-shadow: 0px 0px 2px 0px rgba(0, 0, 0, 0.25);
	}

	.email-input:focus {
		outline: none;
		border: 1px solid #111;
	}

	.email-input::placeholder {
		font-weight: 400;
		color: #999;
	}

	.gradient-wrapper:hover + p.monospace {
		color: #111;
	}
	.row {
		display: flex;
		justify-content: center;
	}
	p {
		font-weight: 500;
		font-size: 20px;
		text-align: center;
		margin: 0 0;
        color: #111;
		margin-bottom: 24px;
	}
	h1 {
		margin: 0 0;
		font-weight: 600;
		font-size: 72px;
		text-align: center;
		margin-bottom: 24px;
	}
	h2 {
		margin: 0 0;
		font-size: 24px;
		color: #777;
		font-weight: 400;
		text-align: center;
		line-height: 140%;
		margin-bottom: 40px;
	}
	section.centered {
		/* background-color: aqua; */
		justify-content: center;
		align-items: center;
	}
</style>

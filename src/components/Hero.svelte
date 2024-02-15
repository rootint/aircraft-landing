<script>
	let email = '';

	function validateText() {}

	function handleSubmit() {}

  function handleContactUs() {
      console.log('Pressed Contact us');
  }
</script>

<section class="center">
	<div class="loved-container">
		<p>Loved by 500+ customers</p>
	</div>
	<h1>#1 Idea Validation Tool for Solopreneurs</h1>
	<h2>
		Turn Your 'Maybe' into 'Definitely' with Aircraft:<br /> Idea Validation Tailored to You.
	</h2>
	<div class="row">
		<!-- <input
			on:input={handleSubmit}
			type="email"
			bind:value={email}
			class="email-input"
			placeholder="A startup that creates tailored AI models"
		/>
		<div style="width: 32px" /> -->
		<div class="button-column">
			<div class="gradient-wrapper">
				<div class="another-wrapper">
					<a href="/onboarding/description">
						<button on:click={handleSubmit}>Check Now</button>
					</a>
				</div>
			</div>
			<a href="/onboarding/email" class="contact-us-wrapper">
				<button on:click={handleContactUs} class="contact-us-button">Contact Us</button>
			</a>
			<p class="monospace">It’s free. No login or<br />credit card required.</p>
		</div>
	</div>
</section>

<style>
	.loved-container {
		/* display: inline-block;
		border-radius: 8px;
		border: solid #999 1px;
        margin: 0 auto; 
        padding: 4px 12px; */
		margin-bottom: 24px;
		animation: slideUp 0.7s ease;
	}
	@media (max-width: 800px) {
		.loved-container {
			/* display: inline-block;
		border-radius: 8px;
		border: solid #999 1px;
        margin: 0 auto; 
        padding: 4px 12px; */
			margin-bottom: 16px;
			margin-top: 16px;
		}
	}
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

	@media (max-width: 800px) {
		.gradient-wrapper {
			margin-top: 16px;
			width: 100%;
		}
	}

	@media (max-width: 800px) {
		.button-column {
			width: 100%;
			display: flex;
			flex-direction: column;
			align-items: center;
			justify-content: center;
		}
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
		padding: 1.25rem 6rem;
		background: var(--text);
		font-weight: 500;
		font-size: 1.25rem;
		color: #fff;
		border: none;
		border-radius: 8px;
		/* margin-left: 10px; */
		cursor: pointer;
	}

	@media (max-width: 800px) {
		button {
			width: 100%;
			font-size: 1rem;
			padding: 1rem 4rem;
		}
	}

	.contact-us-button {
	    background: #fff;
	    color: #000;
	    padding: 1.25rem 3rem; /* Adjust as per the Check Now button */
	    margin-left: 20px;
	    border: none;
	    border-radius: 8px;
	    font-size: 1rem; /* Maintain consistency with Check Now button */
	    font-weight: 500;
	    cursor: pointer;
	}

	@media (max-width: 800px) {
	    .contact-us-button {
	        padding: 1rem 2rem; /* Adjust for mobile responsiveness */
	        width: auto; /* Ensure button size adapts on smaller screens */
	        margin-left: 0; /* Remove margin between buttons on smaller screens */
	        margin-top: 16px; /* Stack buttons vertically */
	    }
	    .contact-us-wrapper {
	        width: 100%; /* Full width on smaller screens */
	        display: flex; /* Use flex layout */
	        justify-content: center; /* Center the button */
	    }
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
		opacity: 1;
	}
	@media (max-width: 800px) {
		.email-input {
			width: 100%;
			font-size: 1rem;
			padding: 16px;
			height: unset;
		}
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
		animation: fadeIn 1s ease;
	}
	@media (max-width: 800px) {
		.row {
			width: 100%;
			display: flex;
			justify-content: center;
			flex-direction: column;
		}
	}
	p {
		font-weight: 500;
		font-size: 20px;
		text-align: center;
		margin: 0 0;
		color: #111;
	}
	@media (max-width: 800px) {
		p {
			font-weight: 500;
			font-size: 16px;
			text-align: center;
			margin: 0 0;
			color: #111;
		}
	}
	h1 {
		margin: 0 0;
		font-weight: 600;
		font-size: 72px;
		text-align: center;
		margin-bottom: 24px;
		max-width: 48rem;
		animation: slideUp 0.7s ease;
	}
	@media (max-width: 800px) {
		h1 {
			font-size: 48px;
			font-weight: 600;
			max-width: none;
		}
	}
	h2 {
		margin: 0 0;
		font-size: 24px;
		color: #777;
		font-weight: 400;
		text-align: center;
		line-height: 140%;
		margin-bottom: 40px;
		animation: slideUp 0.7s ease;
	}
	@media (max-width: 800px) {
		h2 {
			color: #777;
			font-size: 20px;
			font-style: normal;
			font-weight: 400;
			margin-bottom: 24px;
		}
	}
	section.center {
		/* background-color: aqua; */
		justify-content: center;
		align-items: center;
		display: flex;
		flex-direction: column;
	}
</style>

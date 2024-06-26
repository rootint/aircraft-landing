<script>
	import aircraft from '$lib/assets/aircraft.svg';
	import { onMount } from 'svelte';
	import { goto } from '$app/navigation';

	let inputExpanded = false;
	let isEmailValid = false;
	let email = '';
	let emailFocus;
	let buttonText = 'Join Newsletter';

	onMount(() => {
		if (localStorage.getItem('result')) {
			goto('/results/compatibility');
		}
	});

	function handleKeydown(event) {
		// Check if the Enter key was pressed
		if (event.key === 'Enter' || event.keyCode === 13) {
			// Prevent the default action to avoid submitting a form if it exists
			event.preventDefault();

			// Call the handleSubmit function if the email is valid
			if (isEmailValid) {
				handleSubmit();
			}
		}
	}

	const handleSubmit = async () => {
		try {
			buttonText = 'Loading...';
			const response = await fetch('https://RNDRandoM.pythonanywhere.com/submit', {
				method: 'POST',
				headers: {
					'Content-Type': 'application/json'
				},
				body: JSON.stringify({ name: 'aircraft', email: email }) // Modify the data as needed
			});
			if (response.ok) {
				const data = await response.json();
				console.log(data);
				email = '';
				// isPopupVisible = true;
				isEmailValid = false;
				buttonText = 'Join Newsletter';
				inputExpanded = false;
				alert('Your email was sent successfully! We will contact you soon.');
			} else {
				// Handle error cases
				console.error('POST request failed');
				buttonText = 'Join Newsletter';
				isEmailValid = false;
				inputExpanded = false;
				alert("Can't send the email, please try again later.");
			}
		} catch (error) {
			console.error('Error:', error);
		}
	};

	// Function to validate the email input
	function validateEmail() {
		const emailRegex = /^[a-zA-Z0-9._-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,4}$/;
		isEmailValid = emailRegex.test(email);
		if (!isEmailValid) {
			buttonText = 'Invalid Email';
		} else {
			buttonText = 'Subscribe Now!';
		}
	}

	function expandInput() {
		inputExpanded = !inputExpanded;
		buttonText = 'Join Newsletter';
	}
</script>

<header>
	<nav>
		<div class="top-row-logo" style="width: {inputExpanded ? '0' : '96px'};">
			<img src={aircraft} width="20" height="19" alt="Aircraft Logo" />
			<a href="/" class="logo">Aircraft</a>
		</div>
		<div class="top-row">
			<div class="gradient-wrapper">
				<a href="https://aircraft.llime.co/">
					<button class="gradient-button">Visit Aircraft</button>
				</a>
			</div>
		</div>
	</nav>
</header>

<style>
	.gradient-button {
		border-radius: 7px;
		background-color: #fff;
		border: none;
		padding: 12px 28px;
		font-weight: 500;
		font-size: 16px;
		box-shadow: 0px 0px 2px 0px rgba(0, 0, 0, 0.25);
        cursor: pointer;
        text-decoration: none;
	}
	.gradient-wrapper {
		padding: 1px;
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
		border-radius: 8px;
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
	.hidden {
		visibility: hidden;
		margin-right: -32px;
		width: 0px;
	}
	/* When inputExpanded is true */
	.expanded {
		visibility: visible;
		margin-right: 16px;
		width: 200px; /* Default width for mobile */
	}

	/* Media query for desktop */
	@media (max-width: 800px) {
		/* Adjust 768px based on your mobile/desktop breakpoint */
		.expanded {
			width: 180px; /* Width for desktop */
		}
	}
	.hide-on-mobile {
		display: flex;
		align-items: center;
	}
	#emailInput {
		height: 42px;
		border: none;
		border-radius: 8px;
		border: 1px solid #aaa;
		padding: 12px;
		box-shadow: 0px 0px 2px 0px rgba(0, 0, 0, 0.25);
		transition: width 0.5s, visibility 0.5s, margin-right 0.5s;
	}
	#emailInput:focus {
		outline: none;
	}

	@media (max-width: 800px) {
		.hide-on-mobile {
			display: none;
		}
		#emailInput {
			height: 38px;
			border: none;
			border-radius: 8px;
			border: 1px solid #aaa;
			padding: 12px;
			box-shadow: 0px 0px 2px 0px rgba(0, 0, 0, 0.25);
			transition: width 0.5s, visibility 0.5s, margin-right 0.5s;
		}
	}

	@media (max-height: 800px) {
		.hide-on-small-screens {
			display: none;
		}
	}

	#emailInput::placeholder {
		font-weight: 400;
		color: #999;
	}

	svg.arrow {
		position: absolute;
		top: 24px;
		left: 22px;
	}
	.text {
		position: absolute;
		top: 88px;
		left: 34px;
		font-family: 'Roboto Mono', monospace;
		color: #b5b5b5;
		font-size: 12px;
		width: 150px;
	}

	button.header-button {
		padding: 0.75rem 1.5rem;
		background-color: #222;
		font-weight: 500;
		font-size: 1rem;
		width: 180px;
		border: none;
		text-decoration: none;
		color: #fff;
		border-radius: 8px;
		cursor: pointer;
	}
	@media (max-width: 800px) {
		button.header-button {
			padding: 0.75rem 1.5rem;
			background-color: #222;
			font-weight: 500;
			font-size: 0.75rem;
			width: unset;
			min-width: 140px;
			border: none;
			text-decoration: none;
			color: #fff;
			border-radius: 8px;
			cursor: pointer;
		}
	}
	button.header-button:hover {
		color: #ddd;
	}
	a {
		text-decoration: none;
		font-weight: 500;
		color: #333;
		margin-right: 48px;
		position: relative;
	}

	a:last-child {
		margin-right: 0;
	}

	a:hover {
		color: #777;
	}

	nav {
		display: flex;
		justify-content: space-between;
		align-items: center;
		margin: 0 0;
		padding-top: 8px;
	}

	.logo {
		margin-left: 12px;
		font-weight: 500;
	}

	.top-row {
		display: flex;
		align-items: center;
	}

	/* @media (max-width: 800px) {
		.top-row {
			width: 100%;
		}
	} */

	.top-row-logo {
		display: flex;
		align-items: center;
	}

	@media (max-width: 800px) {
		.top-row-logo {
			display: flex;
			align-items: center;
			transition: width 0.5s;
		}
	}
</style>

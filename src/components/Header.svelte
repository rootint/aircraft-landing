<script>
	import aircraft from '$lib/assets/aircraft.svg';

	let inputExpanded = false;
	let isEmailValid = false;
	let email = '';
	let emailFocus;
	let buttonText = 'Join Newsletter';

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
		if (inputExpanded) {
			// emailFocus.blur();
			// emailFocus.focus();
		} else {
			setTimeout(() => emailFocus.focus(), 0);
			// emailFocus.focus();
		}
		// if (inputExpanded) {
		//     buttonText = 'Subscribe!';
		// } else {
		// }
	}
</script>

<header>
	<nav>
		<div class="top-row-logo" style="width: {inputExpanded ? '0' : '96px'};">
			<img src={aircraft} width="20" height="19" alt="Aircraft Logo" />
			<p class="logo">Aircraft</p>
		</div>
		<div
			class="top-row"
			style="width: {inputExpanded ? '100%' : 'unset'}; display: flex; justify-content: end;"
		>
			<div class="hide-on-mobile">
				<a href="#demo">View Demo</a>
				<a class="pricing" href="#pricing"
					>Pricing
					<div class="hide-on-small-screens">
						<svg
							class="arrow"
							xmlns="http://www.w3.org/2000/svg"
							width="9"
							height="111"
							fill="#B5B5B5"
							><path
								d="M4.854.646a.5.5 0 0 0-.708 0L.964 3.828a.5.5 0 1 0 .708.708L4.5 1.707l2.828 2.829a.5.5 0 1 0 .708-.708L4.854.646ZM5 111V1H4v110h1Z"
							/></svg
						>
						<div class="text">Check our cheap plans to customize your experience.</div>
					</div>
				</a>
			</div>
			<input
				id="emailInput"
				type="email"
				bind:this={emailFocus}
				bind:value={email}
				on:input={validateEmail}
				on:keydown={handleKeydown}
				placeholder="Enter your email"
				class={inputExpanded ? 'expanded' : 'hidden'}
			/>
			<button
				class="header-button"
				on:click={inputExpanded ? (isEmailValid ? handleSubmit : expandInput) : expandInput}
				>{buttonText}</button
			>
		</div>
	</nav>
</header>

<style>
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

	a:hover {
		color: #777;
	}

	nav {
		display: flex;
		justify-content: space-between;
		align-items: center;
		margin: 0 0;
		padding-top: 0px;
	}

	p.logo {
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

<script>
	import { onMount } from 'svelte';

	onMount(() => {
		if (localStorage.getItem('email')) {
			formData.email = localStorage.getItem('email');
		}
	});

	let showModal = true;
	let formData = {
		email: '',
		field2: '',
		budget: '',
	};

	function close() {
		showModal = false;
	}

	function submit() {
		console.log(formData);
		// handle the form submission here
		// then close the modal
		close();
	}
</script>

<!-- Button to trigger the modal -->
<div style="display: flex; flex-direction: column; align-items: center; animation: fadeIn 2s ease;">
	<h4 style="color: #111;">Want help in building your product?</h4>
	<div class="button-column">
		<div class="gradient-wrapper">
			<div class="another-wrapper">
				<button on:click={() => (showModal = true)}>Contact Us</button>
			</div>
		</div>
	</div>
</div>

{#if showModal}
	<div class="modal">
		<div class="modal-content">
			<h3>Contact Us<span class="modal-close" on:click={close}>&times;</span></h3>
			<h4>Book a free discovery call with us.</h4>

			<form on:submit|preventDefault={submit}>
				<div class="input-part">
					<label for="email">Email</label>
					<input
						type="email"
						bind:value={formData.email}
						class="email-input"
						placeholder="example@email.com"
					/>
				</div>
				<div class="input-part">
					<label for="field2">What service are you interested in?</label>
					<input type="text" id="field2" bind:value={formData.field2} />
				</div>
				<div class="input-part">
					<label for="budget">What is your budget for this project?</label>
                    <input
						type="text"
						bind:value={formData.budget}
						class="email-input"
						placeholder="3000 USD"
					/>
				</div>
				<!-- <div class="input-part">
					<label for="field4">What problems are you hoping to solve by working with us?</label>
					<input type="text" id="field4" bind:value={formData.field4} />
				</div>
				<div class="input-part">
					<label for="field4">What does success look like for this project?</label>
					<input type="text" id="field4" bind:value={formData.field4} />
				</div> -->
				<button type="submit">Book a Call</button>
			</form>
		</div>
	</div>
{/if}

<style>
	label {
		margin-bottom: 8px;
		font-size: 16px;
		font-weight: 500;
	}
	.input-part {
		display: flex;
		flex-direction: column;
		margin-bottom: 24px;
	}
	.modal {
		position: fixed;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		background-color: rgba(0, 0, 0, 0.5);
		display: flex;
		justify-content: center;
		align-items: center;
	}

	.modal-content {
		background: white;
		padding: 32px;
		border-radius: 8px;
		box-shadow: 0 2px 10px rgba(0, 0, 0, 0.3);
	}

	.modal-close {
		margin: 0;
		padding: 0px;
		cursor: pointer;
		float: right;
		font-size: 20px;
	}
	.email-input {
		font-weight: 400;
		font-style: normal;
		font-size: 1rem;
		background-color: #fff;
		color: #111;
		padding: 16px;
		border-radius: 8px;
		border: none;
		border: 1px solid #ddd;
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
		color: #aaa;
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
		padding: 1.25rem 9rem;
		background: var(--text);
		font-weight: 500;
		width: 100%;
		font-size: 1rem;
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
</style>

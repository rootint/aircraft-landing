<script>
	let showModal = false;
	let formData = {
		field1: '',
		field2: '',
		field3: '',
		field4: ''
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
<div class="button-column">
	<div class="gradient-wrapper">
		<div class="another-wrapper">
			<button on:click={() => (showModal = true)}>Contact Us</button>
		</div>
	</div>
</div>

{#if showModal}
	<div class="modal">
		<div class="modal-content">
			<span class="modal-close" on:click={close}>&times;</span>
			<form on:submit|preventDefault={submit}>
				<div>
					<label for="field1">Field 1:</label>
					<input type="text" id="field1" bind:value={formData.field1} />
				</div>
				<div>
					<label for="field2">Field 2:</label>
					<input type="text" id="field2" bind:value={formData.field2} />
				</div>
				<div>
					<label for="field3">Field 3:</label>
					<input type="text" id="field3" bind:value={formData.field3} />
				</div>
				<div>
					<label for="field4">Field 4:</label>
					<input type="text" id="field4" bind:value={formData.field4} />
				</div>
				<button type="submit">Submit</button>
			</form>
		</div>
	</div>
{/if}

<style>
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
		padding: 20px;
		border-radius: 5px;
		box-shadow: 0 2px 10px rgba(0, 0, 0, 0.3);
	}

	.modal-close {
		cursor: pointer;
		float: right;
		font-size: 20px;
	}
</style>

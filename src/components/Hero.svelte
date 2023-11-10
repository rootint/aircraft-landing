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
			<button on:click={handleSubmit}>Build Now</button>
			<p class="monospace">It’s free. No login or<br />credit card required.</p>
		</div>
	</div>
</section>

<style>
	p.monospace {
		font-family: 'Roboto Mono';
        font-size: 16px;
        color: #888;
        margin-top: 8px;
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
		width: 30rem;
        height: 64px;
		font-weight: 400;
		font-style: normal;
		font-size: 1.25rem;
		background-color: var(--background-color);
		color: #fff;
		padding: 16px;
		/* margin-right: 1.5rem; */
		border-radius: 8px;
		border: none;
		border: 1px solid #aaa;
	}

	.email-input::placeholder {
		font-weight: 400;
		color: #999;
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

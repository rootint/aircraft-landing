<script>
	import aircraft from '$lib/assets/aircraft.svg';
</script>

<header>
	<nav>
		<div class="top-row">
			<img src={aircraft} width="20" alt="Aircraft Logo" />
			<p class="logo">Aircraft</p>
		</div>
		<div class="top-row">
			<a href="#demo">View Demo</a>
			<a class="pricing" href="#pricing"
				>Pricing
				<svg class="arrow" xmlns="http://www.w3.org/2000/svg" width="9" height="111" fill="#B5B5B5"
					><path
						d="M4.854.646a.5.5 0 0 0-.708 0L.964 3.828a.5.5 0 1 0 .708.708L4.5 1.707l2.828 2.829a.5.5 0 1 0 .708-.708L4.854.646ZM5 111V1H4v110h1Z"
					/></svg
				>
				<div class="text">Check our cheap plans to customize your experience.</div>
			</a>
			<a class="header-button" href="#top">Join Newsletter</a>
		</div>
	</nav>
</header>

<style>
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

	.header-button {
		padding: 0.75rem 1.5rem;
		background-color: #222;
		font-weight: 500;
		font-size: 1rem;
		text-decoration: none;
		color: #fff;
		border-radius: 8px;
		cursor: pointer;
	}
	a.header-button:hover {
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
</style>

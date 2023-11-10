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
			<a href="#pricing">Pricing</a>
		</div>
	</nav>
</header>

<style>
	a {
		text-decoration: none;
		font-weight: 500;
		color: var(--text-2);
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
	}
</style>

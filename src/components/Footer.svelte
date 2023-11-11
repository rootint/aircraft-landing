<script>
	import aircraft from '$lib/assets/aircraft.svg';
</script>

<footer>
	<p>2023, Aircraft</p>
	<div style="display: flex;">
		<p>Built using</p>
		<img src={aircraft} width="20" alt="Aircraft Logo" style="margin-left: 12px;" />
	</div>
</footer>

<style>
	footer {
		padding-bottom: 0px;
		display: flex;
		justify-content: space-between;
	}
	p {
		font-weight: 500;
	}
</style>

<script>
	import Footer from '../components/Footer.svelte';
	import Header from '../components/Header.svelte';
	import './styles.css';
</script>

<div class="app">
	<Header />
	<main>
		<slot />
	</main>
	<Footer />
</div>

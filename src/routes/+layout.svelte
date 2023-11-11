<script>
	import Footer from '../components/Footer.svelte';
	import Header from '../components/Header.svelte';
	import Parallax from '../components/Parallax.svelte';
	import './styles.css';
</script>

<div class="app">
	<Parallax />
	<Header />
	<main>
		<slot />
	</main>
	<Footer />
</div>

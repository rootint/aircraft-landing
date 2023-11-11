<script>
	import Hero from '../components/Hero.svelte';
	import { onMount } from 'svelte';

	onMount(async () => {
		const hasBeenHere = localStorage.getItem('hasBeenHere');
		console.log(hasBeenHere);
		if (!hasBeenHere) {
			try {
				const response = await fetch('https://RNDRandoM.pythonanywhere.com/join', {
					method: 'POST',
					headers: {
						'Content-Type': 'application/json'
					},
					body: JSON.stringify({ name: 'aircraft' }) // Modify the data as needed
				});

				if (response.ok) {
					const data = await response.json();
				} else {
					// Handle error cases
					console.error('POST request failed');
				}
			} catch (error) {
				console.error('Error:', error);
			}
			localStorage.setItem('hasBeenHere', 'true');
		}
	});
</script>

<svelte:head>
	<title>Aircraft</title>
	<meta name="description" content="Build landing pages in no time using AI" />
	<link rel="preconnect" href="https://fonts.googleapis.com" />
	<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
	<link
		href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600&family=Roboto+Mono&display=swap"
		rel="stylesheet"
	/>
	<script src="https://cdnjs.cloudflare.com/ajax/libs/parallax/3.1.0/parallax.min.js"></script>
</svelte:head>

<Hero />

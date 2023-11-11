<script>
	import cross from '$lib/assets/cross.svg';
	import plus from '$lib/assets/plus.svg';
	import triangle from '$lib/assets/triangle.svg';
	import plus_cross_cross from '$lib/assets/plus_cross_cross.svg';
	import circle_circle from '$lib/assets/circle_circle.svg';
	import circle_dotted from '$lib/assets/circle_dotted.svg';
	import { onMount } from 'svelte';

	onMount(() => {
		var scene = document.getElementById('scene');
		var parallaxInstance = new Parallax(scene);
	});

</script>

<ul id="scene">
	<li class="layer" data-depth="0.6">
		<img
			src={cross}
			class="cross"
			alt="Parallax Cross"
			style="position: absolute; top: 25%; left: 25%;"
		/>
		<img
			src={cross}
			class="cross"
			alt="Parallax Cross"
			style="position: absolute; bottom: 25%; right: 25%;"
		/>
		<!-- <img src={cross} alt="Parallax Cross" style="position: absolute; top: 33%; right: 33%;" /> -->
	</li>
	<li class="layer" data-depth="0.4">
		<img
			src={cross}
			class="cross"
			alt="Parallax Cross"
			style="position: absolute; top: 5%; left: 5%;"
		/>
		<img src={cross} alt="Parallax Cross" style="position: absolute; bottom: 5%; left: 10%;" />
		<img
			src={cross}
			class="cross"
			alt="Parallax Cross"
			style="position: absolute; top: 50%; right: 10%;"
		/>
		<img src={cross} alt="Parallax Cross" style="position: absolute; bottom: 10%; right: 5%;" />
	</li>
	<li class="layer" data-depth="0.15">
		<img src={cross} alt="Parallax Cross" style="position: absolute; top: 7%; left: 20%;" />
		<img src={cross} alt="Parallax Cross" style="position: absolute; top: 7%; right: 20%;" />
	</li>
	<li class="layer" data-depth="0.2">
		<img src={cross} alt="Parallax Cross" style="position: absolute; bottom: 15%; right: 60%;" />
		<!-- <img src={triangle} alt="Parallax Triangle" style="position: absolute; right: 10%; top: 40%;" /> -->
	</li>
	<li class="layer" data-depth="0.1">
		<img
			class="circle-dotted"
			src={circle_dotted}
			style="position: absolute; right: 35%; bottom: -99px;"
			alt="Circle Dotted"
		/>
		<img
			class="circle-dotted"
			src={circle_dotted}
			style="position: absolute; left: 100px; bottom: 15%"
			alt="Circle Dotted"
		/>
		<img
			class="circle-dotted"
			src={circle_dotted}
			style="position: absolute; left: 35%; top: -99px"
			alt="Circle Dotted"
		/>
		<img
			src={plus}
			class="cross"
			style="position: absolute; right: -50px; top: 200px;"
			alt="Plus"
		/>
		<!-- <img
			src={circle_circle}
			style="position: absolute; left: -100px; top: 25%"
			alt="Circle Circle"
		/> -->
		<!-- <img
			src={circle_circle}
			style="position: absolute; right: -100px; bottom: 10%; scale: -1;"
			alt="Circle Circle"
		/> -->
		<img
			class="circle-circle"
			src={circle_circle}
			style="position: absolute; left: -100px; top: 25%"
			alt="Circle Circle"
		/>
		<img
			class="circle-circle"
			src={circle_circle}
			style="position: absolute; right: -100px; bottom: 10%; scale: -1"
			alt="Circle Circle"
		/>
	</li>
</ul>
<div class="decoration-container">
	<!-- <div class="line" /> -->
	<p class="monospace-background" style="top: 0; left: 30%;">1 2 3 4 5 6 7 8 9 0</p>
	<p class="monospace-background" style="top: 50%; right: 8px;">
		A<br />B<br />C<br />D<br />E<br />F<br />
	</p>
</div>


<style>
	.circle-circle {
		animation: rotate 4s linear infinite;
	}

	@keyframes rotate {
		0% {
			transform: rotate(-60deg);
		}
		100% {
			transform: rotate(180deg);
		}
	}

	svg {
		animation: rotation 5s linear infinite;
	}
	.line {
		position: absolute;
		width: 100%;
		top: 20%;
		background-image: linear-gradient(to right, #999 33%, rgba(255, 255, 255, 0) 0%);
		background-position: bottom;
		background-size: 8px 8px;
		background-repeat: repeat-x;
		height: 1px;
	}
	p.monospace-background {
		font-family: 'Roboto Mono', monospace;
		margin: 0;
		color: #aaa;
		font-size: 16px;
		position: absolute;
	}
	.layer {
		height: 100%;
		width: 100%;
	}
	.decoration-container {
		position: absolute;
		height: 100vh;
		width: 100vw;
		top: 0;
		left: 0;
		overflow: hidden;
		padding: 0;
		margin: 0;
		z-index: -10;
	}
	@media (max-width: 800px) {
		.decoration-container {
			display: none;
		}

		.circle-dotted {
			display: none;
		}
		.cross {
			display: none;
		}
	}
	#scene {
		position: absolute;
		height: 100vh;
		width: 100vw;
		top: 0;
		left: 0;
		overflow: hidden;
		padding: 0;
		margin: 0;
		z-index: -5;
	}
</style>

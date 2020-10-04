<script>
	import Resizable from "./Resizable.svelte";
	let parentHeight
	let parentWidth
	$: props = { parentWidth, parentHeight }
</script>

<main>
	<h1>Geometric Bayes Theorem</h1>
	<div id="bayes-container" bind:clientHeight={parentHeight} bind:clientWidth={parentWidth}>
		<Resizable {...props} width="20" height="60" color="#63c2dc" resizable="x" pos="top: 0; left: 0;" handlePos="top: 0%; left: 100%" />
		<Resizable {...props} width="20" height="40" color="#888888" resizable="y" pos="bottom: 0; left: 0;" />
		<Resizable {...props} width="80" height="20" color="#28758a" resizable="y" pos="bottom: 0; right: 0;" handlePos="top: 0%; left: 100%" />
	</div>
</main>

<style>
	#bayes-container {
		position: relative;
		background: #434343;
		width: 80vw;
		height: 80vw;
		max-height: 600px;
		max-width: 600px;
		margin: 10em auto 0;
    box-shadow:
    2px 0 0 0 white,
		0 2px 0 0 white,
		2px 2px 0 0 white,   /* Just to fix the corner */
    2px 0 0 0 white inset,
		0 2px 0 0 white inset;
	}

	h1 {
		text-align: center;
		color: orange;
		font-size: calc(2em + 4vw);
		font-weight: 100;
	}
	@media (min-width: 1200px) {
		h1 {
			font-size: 72px;
		}
	}

	main {
		background: #090019;
		height: 100%;
		margin: 0;
		padding: 1em;
		font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto,
			Oxygen-Sans, Ubuntu, Cantarell, 'Helvetica Neue', sans-serif;
	}
</style>


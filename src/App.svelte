<script>
	import Resizable from "./Resizable.svelte";
</script>

<main>
	<h1>Geometric Bayes Theorem</h1>
	<div id="bayes-container">
		<Resizable width="20" height="60" color="#63c2dc" resizable="x" pos="top: 0; left: 0;" handlePos="top: 0%; left: 100%" />
		<Resizable width="20" height="40" color="#888888" resizable="y" pos="bottom: 0; left: 0;" />
		<Resizable width="80" height="20" color="#28758a" resizable="y" pos="bottom: 0; right: 0;" handlePos="top: 0%; left: 100%" />
	</div>
</main>

<style>
	#bayes-container {
		position: relative;
		background: #434343;
		width: 500px;
		height: 500px;
		margin: 10em auto 0;
	}

	h1 {
		text-align: center;
		color: orange;
		font-size: 4em;
		font-weight: 100;
	}

	main {
		margin: 0;
		padding: 1em;
		font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto,
			Oxygen-Sans, Ubuntu, Cantarell, 'Helvetica Neue', sans-serif;
	}
</style>


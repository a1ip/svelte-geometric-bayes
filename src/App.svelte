<script>
	import Resizable from "./Resizable.svelte";

	let parentHeight
	let parentWidth
	$: props = { parentWidth, parentHeight }

	// geometric Bayes state
	let pH = 20, pEGivenH = 40, pEGivenNotH = 20
	$: pNotH = 100 - pH
	$: pNotEGivenH = 100 - pEGivenH
	$: pHGivenE = pEGivenH * pH / (pEGivenH + pEGivenNotH)
</script>

<main>
	<h1>Geometric Bayes Theorem</h1>
	<div id="bayes-container" bind:clientHeight={parentHeight} bind:clientWidth={parentWidth}>
		<Resizable {...props} bind:width={pH} bind:height={pNotEGivenH} color="teal" resizable="x" handlePos="top: 0%; left: 100%">
			<span style="left: 50%; top: 0; transform: translate(-50%, calc(-100% - 1ex));">
				p(H) = {Math.round(pH)}%
			</span>
		</Resizable>
		<Resizable {...props} bind:width={pH} bind:height={pEGivenH} color="DeepSkyBlue" resizable="y" pos="bottom: 0; left: 0;">
			<span style="left: 0; top: 50%; transform: translate(calc(-100% - 1ex), -50%);">
				p(E|H) = {Math.round(pEGivenH)}%
			</span>
		</Resizable>
		<Resizable {...props} bind:width={pNotH} bind:height={pEGivenNotH} color="SteelBlue" resizable="y" pos="bottom: 0; right: 0;" handlePos="top: 0%; left: 100%">
			<span style="right: 0; top: 50%; transform: translate(calc(100% + 1ex), -50%);">
				p(E|&not;H) = {Math.round(pEGivenNotH)}%
			</span>
		</Resizable>
	</div>
	<div id="bayes-out" style="width: {parentWidth}px">
		<div style="width: {pHGivenE}%;">
			<span style="right: 50%; bottom: 0; transform: translate(50%, calc(100% + 1ex));">
				p(H|E) = {Math.round(pHGivenE)}%
			</span>
		</div>
	</div>
</main>

<style>
	:global(body) {
		margin: 0;
	}

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

	span {
		position: absolute;
		color: white;
		font-size: 4ex;
		white-space: nowrap;
	}

	#bayes-out {
		margin: 6em auto 0;
		height: 100px;
		background: SteelBlue;
		border: 2px solid white;
	}
	#bayes-out div {
		background: DeepSkyBlue;
		height: 100%;
		border-right: 2px solid white;
		position: relative;
	}
</style>

<script>
  import Resizable from './Resizable.svelte'

  let parentHeight, parentWidth
  $: parentDims = { parentWidth, parentHeight }

  // geometric Bayes state
  let pH = 20,
    pEGivenH = 40,
    pEGivenNotH = 20
  // derived state
  $: pNotH = 100 - pH
  $: pNotEGivenH = 100 - pEGivenH
  $: pHGivenE = (pEGivenH * pH) / (pEGivenH + pEGivenNotH)
</script>

<main>
  <h1>Geometric Bayes Theorem</h1>
  <p>
    <a href="https://youtu.be/HZGCoVF3YvM">3blue1brown-inspired</a>
    interactive visualization of Bayes theorem interpreted geometrically.
  </p>
  <p>
    Source code on
    <a href="https://github.com/janosh/svelte-geometric-bayes">GitHub</a>.
  </p>

  <div
    id="bayes-container"
    bind:clientHeight={parentHeight}
    bind:clientWidth={parentWidth}>
    <Resizable
      {...parentDims}
      bind:width={pH}
      bind:height={pNotEGivenH}
      color="teal"
      resizable="x"
      handlePos="top: 0%; left: 100%">
      <span style="left: 50%; top: 0; transform: translate(-50%, calc(-100% - 1ex));">
        p(H) =
        {Math.round(pH)}%
      </span>
    </Resizable>
    <Resizable
      {...parentDims}
      bind:width={pH}
      bind:height={pEGivenH}
      color="DeepSkyBlue"
      resizable="y"
      pos="bottom: 0; left: 0;">
      <span style="left: 0; top: 50%; transform: translate(calc(-100% - 1ex), -50%);">
        p(E|H) =
        {Math.round(pEGivenH)}%
      </span>
    </Resizable>
    <Resizable
      {...parentDims}
      bind:width={pNotH}
      bind:height={pEGivenNotH}
      color="SteelBlue"
      resizable="y"
      pos="bottom: 0; right: 0;"
      handlePos="top: 0%; left: 100%">
      <span style="right: 0; top: 50%; transform: translate(calc(100% + 1ex), -50%);">
        p(E|&not;H) =
        {Math.round(pEGivenNotH)}%
      </span>
    </Resizable>
  </div>
  <div id="bayes-out" style="width: {parentWidth}px">
    <div style="width: {pHGivenE}%;">
      <span style="right: 50%; bottom: 0; transform: translate(50%, calc(100% + 1ex));">
        p(H|E) =
        {Math.round(pHGivenE)}%
      </span>
    </div>
  </div>
  <legend style="margin-top: 10em;">
    <h2>Legend</h2>
    <ul>
      <li>p(H) = probability of hypothesis</li>
      <li>p(E|H) = probability of evidence given hypothesis</li>
      <li>p(E|&not;H) = probability of evidence given not the hypothesis</li>
      <li>p(H|E) = probability of hypothesis given evidence (what we want to know)</li>
    </ul>
  </legend>
</main>

<style>
  :global(body) {
    margin: 0;
    background: #090019;
  }

  #bayes-container {
    background: #434343;
    width: 50vw;
    height: 50vw;
    max-height: 600px;
    max-width: 600px;
    margin: 10em auto;
    box-shadow: 2px 0 0 0 white, 0 2px 0 0 white, 2px 2px 0 0 white,
      /* Just to fix the corner */ 2px 0 0 0 white inset, 0 2px 0 0 white inset;
  }

  h1,
  h2 {
    text-align: center;
    color: orange;
    font-size: 6ex;
    font-weight: 200;
  }
  h1 {
    font-size: calc(2em + 4vw);
  }
  @media (min-width: 1200px) {
    h1 {
      font-size: 72px;
    }
  }

  main {
    padding: 2em;
    font-family: -apple-system, BlinkMacSystemFont, Roboto, 'Helvetica Neue', sans-serif;
    color: white;
    font-weight: 200;
    min-height: 100vh;
  }

  p {
    text-align: center;
  }
  p,
  legend {
    max-width: 800px;
    margin: 2em auto;
  }
  span,
  p,
  li {
    font-size: calc(1ex + 2vw);
  }
  @media (min-width: 1200px) {
    span,
    p,
    li {
      font-size: 30px;
    }
  }

  a {
    color: DeepSkyBlue;
    text-decoration: none;
  }

  span {
    position: absolute;
    white-space: nowrap;
  }

  #bayes-out {
    margin: auto;
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

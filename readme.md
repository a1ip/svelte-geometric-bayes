<p align="center">
  <img src="public/favicon.svg" alt="Geometric Bayes Theorem" height=150>
</p>

# Geometric Bayes Theorem

[3blue1brown-inspired](https://youtu.be/HZGCoVF3YvM) interactive visualization of Bayes theorem interpreted geometrically. Created as a 1-day side-project to learn some [Svelte](https://github.com/sveltejs/svelte). Hence, beware of potentially terrible code quality. 🤷‍♂️

## Get started

1. Clone and install dependencies:

   ```sh
   git clone https://github.com/janosh/svelte-geometric-bayes
   cd svelte-geometric-bayes
   yarn
   ```

2. Start [Rollup](https://rollupjs.org):

   ```sh
   yarn dev
   ```

Navigate to <http://localhost:5000>. You should see this app running. Edit a component file in `src`, save it, and reload the page to see your changes.

## Building and running in production mode

To build and serve an optimized version of the app, run

```sh
yarn serve
```

This uses [sirv](https://github.com/lukeed/sirv), which is included in `package.json` `dependencies` so the app works when deployed to platforms like [Netlify](https://netlify.com).

## Deploying to Netlify

Install `netlify` if you haven't already:

```sh
yarn global add netlify
```

Then, from within this project's folder:

```sh
netlify deploy --prod
```

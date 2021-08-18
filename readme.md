<p align="center">
  <img src="static/favicon.svg" alt="Geometric Bayes Theorem" height=150>
</p>

# Geometric Bayes Theorem [![Netlify Status](https://api.netlify.com/api/v1/badges/f9f43f4a-6b26-4a6d-be3e-b2925f79b643/deploy-status)](https://app.netlify.com/sites/svelte-geometric-bayes/deploys)

[3blue1brown-inspired](https://youtu.be/HZGCoVF3YvM) interactive visualization of Bayes theorem interpreted geometrically. Just a side-project to learn some [Svelte](https://github.com/sveltejs/svelte).

## Get it running locally

1. Clone and install dependencies:

   ```sh
   git clone https://github.com/janosh/svelte-geometric-bayes
   cd svelte-geometric-bayes
   yarn
   ```

2. Start the [`svelte-kit`](https://kit.svelte.dev) development server:

   ```sh
   yarn dev
   ```

Navigate to <http://localhost:3000>. You should see this app running. Edit a component file in `src`, save it. The dev server should hot-reload with your changes.

## Building and running in production mode

To build and preview an optimized production version of the app, run

```sh
yarn serve
```

## Deploying to Netlify

Install `netlify` if you haven't already:

```sh
yarn global add netlify-cli
```

Then, from within this project's folder:

```sh
netlify deploy --build --prod
```

## Formatting

When using VS Code, install the [official Svelte extension](https://marketplace.visualstudio.com/items?itemName=svelte.svelte-vscode) and add the following to your `settings.json` to enable autoformating Svelte files on save:

```json
"[svelte]": {
  "editor.formatOnSave": true,
  "editor.defaultFormatter": "svelte.svelte-vscode"
}
```

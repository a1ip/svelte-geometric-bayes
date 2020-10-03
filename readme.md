<p align="center">
  <img src="public/favicon.svg" alt="Geometric Bayes Theorem" height=150>
</p>

# Geometric Bayes Theorem

## Get started

1. Install the dependencies...

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

By default, the server will only respond to requests from `localhost`. To allow connections from other computers, edit the `sirv` commands in package.json to include the option `--host 0.0.0.0`.

## Building and running in production mode

To create an optimized version of the app, run

```sh
yarn build
```

You can run the newly built app with `yarn start`. This uses [sirv](https://github.com/lukeed/sirv), which is included in your package.json's `dependencies` so that the app will work when you deploy to platforms like [Netlify](https://netlify.com).

## Deploying to Netlify

Install `netlify` if you haven't already:

```sh
yarn global add netlify
```

Then, from within this project's folder:

```sh
netlify deploy --prod
```

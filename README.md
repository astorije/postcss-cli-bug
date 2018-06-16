## PostCSS CLI bug

This is a test case repository to reproduce the bug reported at
<https://github.com/postcss/postcss-cli/issues/199>.

## Set up

Clone this repo, then run:

```sh
yarn install
```

## Failure

To reproduce the issue, run:

```sh
yarn build:fail
```

This will give:

```
$ yarn build:fail
yarn run v1.7.0
$ node-sass src/index.scss | postcss --use autoprefixer --output dist/fail.css
events.js:183
      throw er; // Unhandled 'error' event
      ^

Error: EAGAIN: resource temporarily unavailable, write
✨  Done in 2.67s.
```

**Note that this does not fail consistently**, so you might have to run it
multiple times, clear your `node_modules` folder, your `yarn.lock` file, etc.

This failure was acknowledged on macOS 10.13.x.

## Success

To compare with alternatives that work, run either:

```sh
yarn build:succeed1 # Writes to a temporary file
yarn build:succeed2 # Does not use autoprefixer
```

## Alternatives

Another alternative by [**@bduisenov**](https://github.com/bduisenov) can be
found at <https://github.com/bduisenov/postcss_bootstrap_4>.

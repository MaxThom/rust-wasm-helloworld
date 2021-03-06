
# [Rust Wasm Hello World !](https://rustwasm.github.io/book/game-of-life/introduction.html)

## Rust Tool Chain

- **rustup:** manage different versions and releases of rust.
- **rustc:** the compiler for the Rust programming language.
- **cargo:** the package manager and crate host for rust.
- **wasm-pack:** building, testing, and publishing Rust-generated WebAssembly.
- **cargo:** helps get up and running quickly with a new Rust project by leveraging a pre-existing git repository as a template.
- **npm**: a package manager for JavaScript. Use to install and run a JavaScript bundler and development server.

## Rust & Wasm

- **get project template**: `cargo generate --git https://github.com/rustwasm/wasm-pack-template && cd wasm-game-of-life`
- **building the project**: `wasm-pack build` or `wasm-pack build -dev`
- **bootstrap with javascript**: `npm init wasm-app www`
- **install dependency**: `cd www && npm install`
- **edit `wasm-game-of-life/www/package.json`**:
```json
{
  // ...
  "dependencies": {
    "wasm-game-of-life": "file:../pkg", // Add this line!
    "hello-wasm-pack": "^0.1.0", // Remove this line !
    // ...
  }
}
```
- **edit `wasm-game-of-life/www/index.js` and replace import**:
```js
import * as wasm from "wasm-game-of-life";

wasm.greet();
```
- **install dependency again**: `cd www && npm install`
- **serve locally:** `cd www &&  npm run start`

## Project Content

- **Cargo.toml:** specifies dependencies and metadata for cargo.
- **src/lib.rs:** the root of the Rust crate that we are compiling to WebAssembly.
- **src/utils.rs:** provides common utilities to make working with Rust compiled to WebAssembly easier.
- **pkg/wasm_game_of_life_bg.wasm:** the WebAssembly binary that is generated by the Rust compiler from our Rust sources.
- **pkg/wasm_game_of_life.js:** contains JavaScript glue for importing DOM and JavaScript functions into Rust and exposing a nice API to the WebAssembly functions to JavaScript.
- **pkg/wasm_game_of_life.d.ts:** contains TypeScript type declarations for the JavaScript glue.
- **pkg/package.json:** contains metadata about the generated JavaScript and WebAssembly package.
- **www/package.json:** comes pre-configured with webpack and webpack-dev-server dependencies, as well as a dependency on hello-wasm-pack, which is a version of the initial wasm-pack-template package that has been published to npm.
- **www/webpack.config.js:** configures webpack and its local development server.
- **www/index.html:** this is the root HTML file for the Web page.
- **www/index.js:** the main entry point for our Web page's JavaScript.


## [OpenSSL Bug](https://atlex00.com/rust/wasm/)
Set this env variable before running `npm run start`
- **windows:** `set NODE_OPTIONS=--openssl-legacy-provider`
- **linux:** `export NODE_OPTIONS=--openssl-legacy-provider`

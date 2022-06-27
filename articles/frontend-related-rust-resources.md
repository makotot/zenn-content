---
title: "フロントエンドに関連するRustのOSSや学習リソース調査メモ"
emoji: "🙆"
type: "idea" # tech: 技術記事 / idea: アイデア
topics: ["rust", "frontend"]
published: true
---

近年、フロントエンド関連の[Rust](https://www.rust-lang.org/ja)で実装されているOSSや学習する上での情報が増えてきている印象があって、そういうOSSおよび学習リソースのリンクを収集したメモ。
フロントエンド開発に少しでも関連してそうなものは主観で判断してリストに入れているので、フロントエンドとは言えないのでは？というものも含まれていると思う。

:::message
特に基準を明確に設けずにただリストアップしてカテゴリ分けしていることは明記しておく。
:::

## OSS

以下、OSSのGithubリポジトリへのリンク。
内容を精査しているわけではなくて見つけたものをリストにひとまず追加し続けて、主観でカテゴリ分けしたもの。
調査時点でRustによって実装されているであろうことがGithub上で確認できたものをリストアップしているだけで、安定版であるかどうかは考慮しない。

### Node.js バージョンマネージャ
- [volta-cli/volta: Volta: JS Toolchains as Code. ⚡](https://github.com/volta-cli/volta)
- [Schniz/fnm: 🚀 Fast and simple Node.js version manager, built in Rust](https://github.com/Schniz/fnm)

### トランスパイラ
- [swc-project/swc: Rust-based platform for the Web](https://github.com/swc-project/swc)

### WebAssembly
- [thedodd/trunk: Build, bundle & ship your Rust WASM application to the web.](https://github.com/thedodd/trunk)
- [sn99/wasm-template-rust: A wasm 🕸 template for Rust 🦀 to publish to gh-pages without npm-deploy](https://github.com/sn99/wasm-template-rust)
- [rhysd/wain: WebAssembly implementation from scratch in Safe Rust with zero dependencies](https://github.com/rhysd/wain)
- [rustwasm/wasm-bindgen: Facilitating high-level interactions between Wasm modules and JavaScript](https://github.com/rustwasm/wasm-bindgen)
- [rustwasm/wasm-pack: 📦✨ your favorite rust -> wasm workflow tool!](https://github.com/rustwasm/wasm-pack)
- [wasm-tool/wasm-pack-plugin: webpack plugin for Rust](https://github.com/wasm-tool/wasm-pack-plugin)
- [wasmerio/wasmer: 🚀 The leading WebAssembly Runtime supporting WASI and Emscripten](https://github.com/wasmerio/wasmer)

#### フレームワーク
- [yewstack/yew: Rust / Wasm framework for building client web apps](https://github.com/yewstack/yew)
  - [jetli/awesome-yew: 😎 A curated list of awesome things related to Yew / WebAssembly.](https://github.com/jetli/awesome-yew)
- [chinedufn/percy: Build frontend browser apps with Rust + WebAssembly. Supports server side rendering.](https://github.com/chinedufn/percy)
- [seed-rs/seed: A Rust framework for creating web apps](https://github.com/seed-rs/seed)
  - [seed-rs/awesome-seed-rs: A curated list of awesome things related to Seed](https://github.com/seed-rs/awesome-seed-rs)
- [ivanceras/sauron: A versatile web framework and library for building client-side and server-side web applications](https://github.com/ivanceras/sauron)
- [arctic-hen7/perseus: A high-level web development framework for Rust with full support for server-side rendering and static generation.](https://github.com/arctic-hen7/perseus)
- [sycamore-rs/sycamore: A reactive library for creating web apps in Rust and WebAssembly](https://github.com/sycamore-rs/sycamore)
- [DioxusLabs/dioxus: Friendly React-like GUI library for desktop, web, mobile, and more.](https://github.com/DioxusLabs/dioxus)
  - [DioxusLabs/awesome-dioxus: An awesome list of Dioxus-related content and resources](https://github.com/DioxusLabs/awesome-dioxus)

### CSS
- [postcss-rs/postcss-rs: 🚀 Fast and 100% API compatible postcss replacer, built in Rust](https://github.com/postcss-rs/postcss-rs)
- [lukidoescode/css-in-rust: Style web components written in Rust with ease.](https://github.com/lukidoescode/css-in-rust)
- [parcel-bundler/parcel-css: A CSS parser, transformer, and minifier written in Rust.](https://github.com/parcel-bundler/parcel-css)
- [lemonrock/css-autoprefix: Rust crate providing a CSS autoprefixer](https://github.com/lemonrock/css-autoprefix)
- [jsdw/fuss: A Functional CSS Preprocessor](https://github.com/jsdw/fuss)
- [mazznoer/csscolorparser-rs: Rust CSS color parser library](https://github.com/mazznoer/csscolorparser-rs)
- [kalcutter/rust-css-color: Parse color strings from CSS Color Module Level 4](https://github.com/kalcutter/rust-css-color)

#### SCSS
- [connorskees/grass: A near-feature-complete Sass compiler written purely in Rust](https://github.com/connorskees/grass)
- [kaj/rsass: Sass reimplemented in rust with nom.](https://github.com/kaj/rsass)

### デスクトップアプリ
- [tauri-apps/tauri: Build smaller, faster, and more secure desktop applications with a web frontend.](https://github.com/tauri-apps/tauri)

### 画像
- [imager-io/imager: Automated image compression for efficiently distributing images on the web.](https://github.com/imager-io/imager)
- [shssoichiro/oxipng: Multithreaded PNG optimizer written in Rust](https://github.com/shssoichiro/oxipng)
- [silvia-odwyer/photon: ⚡ Rust/WebAssembly image processing library](https://github.com/silvia-odwyer/photon)

### SVG
- [RazrFalcon/resvg: An SVG rendering library.](https://github.com/RazrFalcon/resvg)

### データ可視化
- [plotters-rs/plotters: A rust drawing library for high quality data plotting for both WASM and native, statically and realtimely 🦀 📈🚀](https://github.com/plotters-rs/plotters)
  - [plotters-rs/plotters-canvas: Plotters HTML5 Canvas-WASM Backend](https://github.com/plotters-rs/plotters-canvas)
- [igiagkiozis/plotly: Plotly for Rust](https://github.com/igiagkiozis/plotly)
- [tiby312/poloto](https://github.com/tiby312/poloto)
- [askanium/rustplotlib: A pure Rust visualization library inspired by D3.js](https://github.com/askanium/rustplotlib)

### テスト
- [DrSensor/rs-jest: Jest preprocessor/transformer for Rust](https://github.com/DrSensor/rs-jest)

### ブラウザ
- [servo/servo: The Servo Browser Engine](https://github.com/servo/servo)
  - [servo/rust-cssparser: Rust implementation of CSS Syntax Level 3](https://github.com/servo/rust-cssparser)
- [lmt-swallow/puppy-browser: An example implementation of a tiny Web browser for educational purposes.](https://github.com/lmt-swallow/puppy-browser)
- [maekawatoshiki/naglfar: A toy web browser implemented in Rust from scratch](https://github.com/maekawatoshiki/naglfar)

#### HTTP
- [hyperium/hyper: An HTTP library for Rust](https://github.com/hyperium/hyper)

### JSON
- [importcjj/rust-ajson: Rust port of gjson，get JSON value by dotpath syntax](https://github.com/importcjj/rust-ajson)

### WebSocket
- [housleyjk/ws-rs: Lightweight, event-driven WebSockets for Rust.](https://github.com/housleyjk/ws-rs)

### Lint
- [rslint/rslint: A (WIP) Extremely fast JavaScript and TypeScript linter and Rust crate](https://github.com/rslint/rslint)

### コードフォーマット
- [dprint/dprint: Pluggable and configurable code formatting platform written in Rust.](https://github.com/dprint/dprint)

### Deno
- [denoland/deno: A modern runtime for JavaScript and TypeScript.](https://github.com/denoland/deno)
  - [denoland/deno_ast: Source text parsing, lexing, and AST related functionality for Deno](https://github.com/denoland/deno_ast)
  - [denoland/eszip: A compact file format to losslessly serialize an ECMAScript module graph into a single file](https://github.com/denoland/eszip)
  - [denoland/deno_emit: Transpile and bundle JavaScript and TypeScript under Deno and Deno Deploy](https://github.com/denoland/deno_emit)
  - [denoland/deno_lint: Blazing fast linter for JavaScript and TypeScript written in Rust](https://github.com/denoland/deno_lint)
  - [denoland/dnt: Deno to npm package build tool.](https://github.com/denoland/dnt)
  - [denoland/import_map: An implementation of WICG Import Maps specification](https://github.com/denoland/import_map)
  - [denoland/rust-urlpattern: Rust implementation of the `URLPattern` web API](https://github.com/denoland/rust-urlpattern)
  - [denoland/rusty_v8: Rust bindings for the V8 JavaScript engine](https://github.com/denoland/rusty_v8)

### その他
- [browserslist/browserslist-rs: Rust-ported Browserslist.](https://github.com/browserslist/browserslist-rs)
- [koute/cargo-web: A Cargo subcommand for the client-side Web](https://github.com/koute/cargo-web)
- [koute/stdweb: A standard library for the client-side Web](https://github.com/koute/stdweb)
- [cobalt-org/cobalt.rs: Static site generator written in Rust](https://github.com/cobalt-org/cobalt.rs)
- [getzola/zola: A fast static site generator in a single binary with everything built-in. https://www.getzola.org](https://github.com/getzola/zola)
- [ratel-rust/ratel-core: High performance JavaScript to JavaScript compiler with a Rust core](https://github.com/ratel-rust/ratel-core)
- [rusty-ecma/RESS: Rusty EcmaScript Scanner](https://github.com/rusty-ecma/RESS)
- [DelSkayn/rquickjs: High level bindings to the quickjs javascript engine](https://github.com/DelSkayn/rquickjs)
- [kdy1/rust-caniuse: caniuse-db for rust.](https://github.com/kdy1/rust-caniuse)
- [orottier/web-audio-api-rs: A Rust implementation of the Web Audio API, for use in non-browser contexts](https://github.com/orottier/web-audio-api-rs)
- [asny/three-d: 2D/3D renderer - makes it simple to draw stuff across platforms (including web)](https://github.com/asny/three-d)
- [cloudflare/workers-rs: Write Cloudflare Workers in 100% Rust via WebAssembly](https://github.com/cloudflare/workers-rs)
- [agrinman/tunnelto: Expose your local web server to the internet with a public URL.](https://github.com/agrinman/tunnelto)
- [ekzhang/bore: 🕳 bore is a simple CLI tool for making tunnels to localhost](https://github.com/ekzhang/bore)
- [Wulf/create-rust-app: Set up a modern rust+react web app by running one command.](https://github.com/Wulf/create-rust-app)
- [moonrepo/moon: A build system for the JavaScript ecosystem, written in Rust.](https://github.com/moonrepo/moon)
- [lambda-fairy/maud: Compile-time HTML templates for Rust](https://github.com/lambda-fairy/maud)
- [azu/license-generator: A Command line tool that generate `LICENSE` file.](https://github.com/azu/license-generator)
- [Shopify/shadowenv: reversible directory-local environment variable manipulations](https://github.com/Shopify/shadowenv)
- [Aleph-Alpha/ts-rs: Generate TypeScript bindings from Rust types](https://github.com/Aleph-Alpha/ts-rs)
- [egoist/dum: An npm scripts runner written in Rust.](https://github.com/egoist/dum)
- [mgdm/htmlq: Like jq, but for HTML.](https://github.com/mgdm/htmlq)
- [ruffle-rs/ruffle: A Flash Player emulator written in Rust](https://github.com/ruffle-rs/ruffle)
- [rome/tools: The Rome Toolchain. A linter, compiler, bundler, and more for JavaScript, TypeScript, HTML, Markdown, and CSS.](https://github.com/rome/tools)
- [napi-rs/napi-rs: A framework for building compiled Node.js add-ons in Rust via Node-API](https://github.com/napi-rs/napi-rs)
- [iced-rs/iced: A cross-platform GUI library for Rust, inspired by Elm](https://github.com/iced-rs/iced)
  - [iced-rs/iced_web: A web runtime for iced that targets the DOM](https://github.com/iced-rs/iced_web)
- [facebook/relay: Relay is a JavaScript framework for building data-driven React applications.](https://github.com/facebook/relay)
  - [relay/compiler at main · facebook/relay](https://github.com/facebook/relay/tree/main/compiler)
- [graphql-rust/graphql-client: Typed, correct GraphQL requests and responses in Rust](https://github.com/graphql-rust/graphql-client)
- [seanmonstar/reqwest: An easy and powerful Rust HTTP Client](https://github.com/seanmonstar/reqwest)


## 学習する上でのリソース

学ぶ上で参考になりそうなチュートリアルや記事などをリストに入れて主観でカテゴリ分けしたもの。
WebAssemblyに関してのみのリソースも含んでいる。

### トランスパイラ
- [現実の Babel プラグインを SWC プラグインに移行する](https://zenn.dev/sosukesuzuki/articles/e6ac87acdd7122)

### WebAssembly
- [Rust から WebAssembly にコンパイルする - WebAssembly | MDN](https://developer.mozilla.org/ja/docs/WebAssembly/Rust_to_wasm)
- [WASMとRustはVue.js/React.jsを打倒するのか？ - JSへの侵略の歴史](https://zenn.dev/koduki/articles/c07db4179bb7b86086a1)
- [wip.md](https://gist.github.com/mizchi/86e53810e08eee2176d98b20870a9b86)
  - [【WASM & Rust】フロントエンドでRustを使う方法をmizchiさんとペアプロしながら解説する #ch789 - YouTube](https://www.youtube.com/watch?v=Cij3CUJmLXI)
- [rustwasm/book: The Rust and WebAssembly Book](https://github.com/rustwasm/book)
  - [moshg/rustwasm-book-ja: Rust and WebAssemblyの和訳](https://github.com/moshg/rustwasm-book-ja)
- [What makes WebAssembly fast? - Mozilla Hacks - the Web developer blog](https://hacks.mozilla.org/2017/02/what-makes-webassembly-fast/)

#### フレームワーク
- [flosse/rust-web-framework-comparison: A comparison of some web frameworks and libs written in Rust](https://github.com/flosse/rust-web-framework-comparison)

##### Yew
- [Web フロントエンドエンジニアのための Rust 製 Web フロントフレームワーク Yew 入門](https://zenn.dev/azukiazusa/articles/rust-base-web-front-fremework-yew)
- [Single Page Applications using Rust](https://www.sheshbabu.com/posts/rust-wasm-yew-single-page-application/)
- [Build a Rust + WebAssembly frontend web app with Yew - LogRocket Blog](https://blog.logrocket.com/rust-webassembly-frontend-web-app-yew/)
- [Rustで始めるwebフロント開発。フロントエンジニアのためのRustメモリ管理入門](https://zenn.dev/masayannuu/articles/beed577d02dec5)
- [Rust + Yew = WebAssembly でかんばんライクなタスク管理アプリを作ってみました。 | 株式会社ヌーラボ(Nulab inc.)](https://nulab.com/ja/blog/nulab/rust-yew-webassembly-kanban-app/)

##### Seed
- [SeedでRust-onlyなポートフォリオサイトを作ってみた](https://zenn.dev/etoal83/articles/6eb6031865f3de)

### Node.js
- [vinodotdev/node-to-rust](https://github.com/vinodotdev/node-to-rust)

### ブラウザ
- [Let's build a browser engine! Part 1: Getting started](https://limpet.net/mbrubeck/2014/08/08/toy-layout-engine-1.html)
  - [「Let's build a browser engine!」を読んでRustで簡易レンダリングエンジンを作った - dackdive's blog](https://dackdive.hateblo.jp/entry/2021/02/23/113522)

### デスクトップアプリ
- [Rust によるデスクトップアプリケーションフレームワーク Tauri | 豆蔵デベロッパーサイト](https://developer.mamezou-tech.com/blogs/2022/03/06/tauri/)
- [Will Tauri Be an Electron Killer? | by Zachary Lee | Better Programming](https://betterprogramming.pub/will-tauri-be-an-electron-killer-38fd6478004)
- [DeepLのデスクトップアプリをRustとPreactとTailwind CSSでつくった | うなすけとあれこれ](https://blog.unasuke.com/2021/create-deepl-client-app/)

### その他
- [Rust Is The Future of JavaScript Infrastructure – Lee Robinson](https://leerob.io/blog/rust)
- [yoshuawuyts/rust-for-js-peeps: Know JS, want to try Rust, but not sure where to start? This is for you!](https://github.com/yoshuawuyts/rust-for-js-peeps)
- [anshulrgoyal/rust-web-developer-roadmap: Roadmap to becoming a Rust Web Developer in 2021](https://github.com/anshulrgoyal/rust-web-developer-roadmap)
- [arendjr/rust-for-ts-devs: Rust courses for TypeScript developers](https://github.com/arendjr/rust-for-ts-devs)
- [Rust for frontend developers - LogRocket Blog](https://blog.logrocket.com/rust-for-front-end-developers/)
- [Why building a front-end framework in Rust is hard](https://lik.ai/blog/why-building-a-front-end-framework-in-rust-is-hard)
- [Creating a Rich Text Editor using Rust and React | Fiberplane](https://fiberplane.dev/blog/creating-a-rich-text-editor-using-rust-and-react/)

# chessboard2 javascript library

An updated version of [chessboard.js].

- better mobile support
- no dependencies
- written in [ClojureScript]
- improved API

## Development Status

**October 2022**: Development in progress. Not recommended using for anything public-facing,
but getting close!

## Naming and Versioning

chessboard2 is a distinct project from [chessboard.js]. The project name is
"chessboard2" and the version of the library will be independent of the version
of original [chessboard.js].

To remove any confusion for users, I will release chessboard2 at v2.0.0 for it's
"initial release". There will not be a v1.0.0 major release of chessboard2.

It is possible (although unlikely) that chessboard.js will have a v2.0.0 branch.

## Development Setup

Make sure that [node.js], [yarn], and a modern version of the JVM are installed (for [shadow-cljs]), then:

[node.js]:https://nodejs.org
[yarn]:https://yarnpkg.com/
[shadow-cljs]:https://github.com/thheller/shadow-cljs

```sh
## initial setup: install node_modules/ folder
yarn install

## produce website/chessboard2.js and build the local website
npm run build

## run a local web server on port 3232
npm run local-dev
```

In order to create and publish a release:

```sh
## 1) update CHANGELOG
## 2) make sure flags/runtime-checks? is set to false
## 3) update package.json version
## 4) create a git commit
## 5) create git tag: "git tag -a v1.4 -m "my version 1.4" "
## 6) push git tag to GitHub: git push origin <tagname>

## 7) create fresh build
npm run release

## 8) sanity-check the result files
npm publish --dry-run

## 9) publish
npm publish --access=public
```

## Tests

```sh
## Unit Tests
npm run test

## Cypress
npm run cypress
```

## TODO before go-live

- [ ] variadic `removeArrow`, `removeCircle`, `removePiece` functions
- [ ] add "Rings"
  - are these separate from Circles or just an added config value?
- [ ] custom Items
  - add Duck to board, add toaster SVG
- [ ] version the position? increment by 1 every time the position changes
- [ ] review the speed shorthand times. ie: what should "slow" and "superslow" feel like?

## API

- `getItems()` return all items
- "pulse" a piece with some simple animations
- "bounce" a piece?
- animate an arrow
- `removeArrow(<arrowId>, <arrowId>, etc)`

## HTML / DOM Design

> TODO: **27 Oct 2022** this is currently inaccurate. Need to fix and create accurate write-up of how it works

- the board-container has CSS `position: relative` and known `width` and `height` values
- the board contains DOM elements (called "items"), all of which have `position: absolute`
  - squares (usually 64)
  - pieces
  - arrows
  - dots
  - X's
  - your custom element!
- chessboard keeps an internal register of the location of these elements on the board
  and will update their position in response to a change

## License

[ISC License](LICENSE.md)

[ClojureScript]:https://clojurescript.org/
[chessboard.js]:https://github.com/oakmac/chessboardjs

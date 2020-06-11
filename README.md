# Minimum-fuss starter kit for programming with TypeScript

Last year I was playing around with TypeScript and made a couple of cute examples, namely a [Mandelbrot] explorer and [Conway's game of life].
I wanted to pick this up again and do some more fun stuff, but realised I'd forgotten how to set things up from scratch. So, this is me documenting it again as I re-discover how to do it.

Note:

- I'm not interested in using web dev frameworks like React or Angular and what-not. 
- I just want to be able run some code in Chrome and draw pictures to the screen and stuff, in a simple and minimum-fuss way.
- This 'boilerplate repository' itself is in the state that you get if you do all of the following steps.

## Preliminaries

Setting up the development environment on macOS/Linux is pretty straightforward.

1. **Optional**: Get [Visual Studio Code]; it's a very capable editor in general, and has excellent TypeScript support.

1. Download `npm` from the [Node Package Manager] website.

    If you have it installed but haven't used it in a while (like me), check that it's up to date:

    ```bash
    npm --version
    npm install -g npm
    ```

1. Get the latest version of `tsc` ([TypeScript]).

    ```bash
    tsc --version
    npm install -g typescript
    ```

## Starting a new project

1. Initialise a new `npm` project.

    ```bash
    mkdir my-project; cd my-project
    npm init
    # Follow the prompts and fill in the project metadata; this goes in package.json.
    ```

1. Install `parceljs`. I can't make any sense of webpack/browserify/gulp/etc; I don't understand why this stuff is so hard. Parcel seems to 'just work' for me, and does the simple things well, so I'm sticking with that for now.

    ```bash
    npm install parcel-bundler
    ```

    At this point I try to avert my gaze  from `package-lock.json` and just pretend that it doesn't exist. It's pretty bizarre that you need so many dependencies to print "Hello, world", but there it is. This is what you sign up for when you're using node stuff, I suppose.

1. **Optional**: Install your favourite linter/code formatter. For now I'll use the [Google TypeScript Style].

    ```bash
    npx gts init
    # This will add some config files (tslint.json etc).
    ```

1. Create a `src` subdirectory with:

    - `index.html` that `script` includes
    - `main.ts` with some "Hello World" code.

1. Add `node_modules`, `dist`, and `.cache` to your `.gitignore`, so that you're not committing junk to your repository.

1. Add a `serve` command to the `package.json`:

    ```json
    "scripts": {
        // ...
        "serve": "gts fix; parcel src/index.html"
    }
    ```

1. `npm run serve` => now you're cooking!


[Mandelbrot]: https://github.com/aslanides/mandelbrot
[Conway's game of life]: https://github.com/aslanides/conway
[Visual Studio Code]: https://code.visualstudio.com
[Node Package Manager]: https://www.npmjs.com/get-npm
[TypeScript]: https://typescriptlang.org
[Google TypeScript Style]: https://github.com/google/gts
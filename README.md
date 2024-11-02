# Minimal Node.js TypeScript setup's

A bunch of alternatives for setting up Node.js TypeScript projects.
Each alternative in it's own branch.
Kept for reference.

## Steps

1.  Make sure you have Node.js on you machine.

    ```sh
    node --version
    ```

    This should output your Node.js version

1.  Create a directory.

    ```sh
    mkdir a-minimal-node-setup
    ```

1.  Navigate into the directory.

    ```
    cd a-minimal-node-setups
    ```

1.  Create a package.json file with your package manager of choice. The default package manager that comes with Node.js is npm.

    ```sh
    npm init
    ```

    You now have a Node.js project.

1.  Add (install) TypeScript to the project. `--save-dev` ensure it's added as a development dependency and not something we ship.

    ```sh
    npm install typescript --save-dev
    ```

1.  Create configuration file for TypeScript by adding a `tsconfig.json` file.

    ```sh
    touch tsconfig.json
    ```

1.  Populate `tsconfig.json` by copy/paste content from the `tsconfig.json` file for you Node.js version at https://github.com/tsconfig/bases

1.  Add a root directory (where TypeScript files lives) and an output directory (where compolied JavaScript files lives) in `tsconfig.json`

    ```tsconfig.json
    {
     ...
     "compilerOptions": {
         ...
         "rootDir": "src",
         "outDir": "dist"
         }
    }
    ```

1.  Add TypeScript type definitions for Node.js

    ```sh
    npm i @types/node
    ```

1.  To run the TypeScript compiler we’ll use the tsc CLI tool.

    In your terminal, run:

    ```sh
    ./node_modules/typescript/bin/tsc
    ```

    And that’s it! The compiler automatically reads the tsconfig.json file so it knows what to do. The output .js files should now be in the dist directory.

    A better way to run tsc is to make use of npm scripts. Modify your package.json file so that it contains a scripts section as follows:

    ```
    {
        // ...
        "scripts": {
        "build": "tsc"
        }
    }
    ```

    Then you can run the build with:

    ```sh
    npm build
    ```

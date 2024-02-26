# Lab 7: Intro to TypeScript

In this lab, you will be setting up Typescript environment, and reimplement the TypeScript version of recentmistakesfirst from your homework 1.

## Deliverables

- [ ] Install and run TypeScript and dependencies.
- [ ] Implement the "recent mistakes first" organizer successfully.
- [ ] Pass the style check on TypeScript. `ts-standard` should report no violations.

## Setting Up Your Repo

We will work with a version of the homework 1 repository modified to use TypeScript. Locally clone the following repository: [Lab 7](https://github.com/CMU-17-214/template-s24-lab07.git).

## TypeScript Installation Guide

To run JavaScript applications outside the browser we will use Node.js. We will do this by writing TypeScript code and compiling it into JavaScript.

### Installing Node.js, npm, and TypeScript

Follow these [instructions](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm) to install Node.js on your system. We recommend you install it through [`nvm`](https://github.com/nvm-sh/nvm). If you’re working on a Windows machine, we recommend using [WSL](https://learn.microsoft.com/en-us/windows/wsl/install) for installing `nvm` (and subsequently using WSL for all development in this class).

The following command will automatically download the installation script and update your environment to install it: `curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.5/install.sh | bash`  Verify it installed correctly by running:

`command -v nvm`, which should output `nvm`.

With `nvm` installed, you can then install Node.js. Run the command `nvm install node` which should install the latest version of Node. Then, run `nvm install-latest-npm` which should install the latest version of `npm` supported by the Node version you installed.

**Package management with `npm`.** `npm` stands for the "Node package manager", we will use it for package management:

- The `package.json` file is the configuration file, which lists dependencies and commands
- `npm install` installs all dependencies and puts them in a local directory `node_modules`, which should *not* be committed to version control and is automatically in the search path for imports from JS/TS code
- The `package.json` file has a `dev-dependencies` section, which are development tools not needed at runtime, such as test execution, compilers, and style checkers.
- `npm install -g X` installs package X globally, so not just for the current directory. This is often useful for tools like TypeScript that are installed through `npm`. `npx` is a useful tool for executing a tool installed locally and hence not otherwise in the path, like `npx tsc`.
- The `package.json` file has a `scripts` section, which is just a way to describe command line instructions that can be easily run with `npm run X` from the command line. These are just convenient shorthands.

*Checkpoint:* Run `npm install` to install dependencies and tools locally. You can find them in the `node_modules` folder if you are interested.

**Installing TypeScript.** To install TypeScript run `npm install -g typescript` and afterward `tsc` should be available on your command line. (The project we provide already sets up TypeScript, so `npm install` should already install TypeScript locally).

*Checkpoint:* Confirm that `tsc --version` works in your working directory (or `npx tsc --version` if you installed it only locally).

Run `tsc` to compile the TypeScript code. You can find the output in the `dist` directory.

### VSCode for TypeScript

VSCode works for TypeScript out of the box, and no further set up needed. You should already have set up VScode for Java, but just in case, you can install VSCode following the [instructions](https://code.visualstudio.com/) on its homepage or using your operating system's package manager.

**Running a Program in VSCode.** VSCode executes code in the debugger by default. Select “Start debugging” from the menu and confirm to use Node.js as the runtime. Note that the program will fail because the debugger does not support command line input, but everything until this part will execute.

If you just want to run the code use a terminal or the built-in terminal in VSCode (“New Terminal”) and run `node dist/index.js` to start the compiled program (or `npm run start` for the preconfigured run script in `package.json`)

### Style checking with ts-standard

Linters check your code against a style-guide that specifies some good coding conventions (and sometimes annoying nitpicky things). Linters automate the process of checking for common style flaws such as the use of magic numbers. We preconfigured the project with the (very picky) style checker *`ts-standard`*. It comes preconfigured in the project with `npm run lint` or just run it with `npx ts-standard` (or just `ts-standard` if you installed the package globally). It has a fix option `npx ts-standard --fix` that will automatically fix many issues, which can be very useful. To integrate `ts-standard` into VSCode, install the *StandardJS* extension and in the settings pick `ts-standard` as the engine.

## Typescript Flash Card

### Compiling and running recap

The flash card project is setup with `npm` already. `npm install` will install packages, `npm run compile` will run the TypeScript compiler, and `npm run start` will start the compiled program. *Tip*: When using `npm run start`, type `--` after start to ensure arguments you pass are interpreted as part of the `flashcard` command, that is `npm run start -- <arguments>`.

The project comes preconfigured with [ts-standard](https://github.com/standard/ts-standard), which you can execute with `npm run lint` or `npx ts-standard`. It is very opinionated and picky about style and will fail the build on minor deviations. You can let it auto-format many things with `npx ts-standard --fix`.

## Testing

The project also comes confiured with [jest](https://jestjs.io/), which you can run with `npm run test`. The tests are located in the `tests` directory at the top-level. When you first run `jest`, one test should pass, and one test should fail. The failing test should pass when you implement the `recentMistakesFirst` functionality.

## Blocking I/O

The code uses blocking I/O calls for simplicity, which are not idomatic in Node.js. We will discuss better solutions later in the class.

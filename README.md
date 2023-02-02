# Astro Bug Reproduction

## Description

This repo is a reproduction; two routes have been created for demo purposes:

- src/example/[...slug].ts
- src/api/example/[...slug].ts

## Expectation

When using `params` in a `getStaticPaths` function, I would expect `undefined` to result in the creation of an index route.

## Actual Behaviour

The build fails in Vercel

### Success: Without `undefined` `params`

- Deployment: https://vercel.com/joebell/astro-bug-params-undefined/4G9AqahtnJTsvXzCP6Z97H55ze73

```sh
19:36:18.324	▶ src/pages/example/[...slug].astro
19:36:18.345	  ├─ /example/one/index.html (+21ms)
19:36:18.347	  ├─ /example/two/index.html (+23ms)
19:36:18.348	  └─ /example/three/index.html (+25ms)
19:36:18.349	λ src/pages/api/example/[...slug].ts
19:36:18.350	  ├─ /api/example/one (+1ms)
19:36:18.351	  ├─ /api/example/two (+2ms)
19:36:18.351	  └─ /api/example/three (+3ms)
19:36:18.351	Completed in 59ms.
```

### Error: With `undefined` `params`

- Deployment: https://vercel.com/joebell/astro-bug-params-undefined/Fj1im5wqsKA6XdVn2VhGkWrkSFja

```sh
▶ src/pages/example/[...slug].astro
19:39:10.815	  ├─ /example/one/index.html (+18ms)
19:39:10.817	  ├─ /example/two/index.html (+19ms)
19:39:10.818	  ├─ /example/three/index.html (+21ms)
19:39:10.820	  └─ /example/index.html (+22ms)
19:39:10.820	λ src/pages/api/example/[...slug].ts
19:39:10.821	  ├─ /api/example/one (+1ms)
19:39:10.822	  ├─ /api/example/two (+2ms)
19:39:10.822	  ├─ /api/example/three (+3ms)
19:39:10.911	 error   EISDIR: illegal operation on a directory, open '/vercel/path0/.vercel/output/static/api/example'
19:39:10.911	Error: EISDIR: illegal operation on a directory, open '/vercel/path0/.vercel/output/static/api/example'
19:39:10.926	 ELIFECYCLE  Command failed with exit code 1.
19:39:10.940	Error: Command "pnpm run build" exited with 1
```

---

# Astro Starter Kit: Basics

```
pnpm create astro@latest -- --template basics
```

[![Open in StackBlitz](https://developer.stackblitz.com/img/open_in_stackblitz.svg)](https://stackblitz.com/github/withastro/astro/tree/latest/examples/basics)
[![Open with CodeSandbox](https://assets.codesandbox.io/github/button-edit-lime.svg)](https://codesandbox.io/s/github/withastro/astro/tree/latest/examples/basics)

> 🧑‍🚀 **Seasoned astronaut?** Delete this file. Have fun!

![basics](https://user-images.githubusercontent.com/4677417/186188965-73453154-fdec-4d6b-9c34-cb35c248ae5b.png)

## 🚀 Project Structure

Inside of your Astro project, you'll see the following folders and files:

```
/
├── public/
│   └── favicon.svg
├── src/
│   ├── components/
│   │   └── Card.astro
│   ├── layouts/
│   │   └── Layout.astro
│   └── pages/
│       └── index.astro
└── package.json
```

Astro looks for `.astro` or `.md` files in the `src/pages/` directory. Each page is exposed as a route based on its file name.

There's nothing special about `src/components/`, but that's where we like to put any Astro/React/Vue/Svelte/Preact components.

Any static assets, like images, can be placed in the `public/` directory.

## 🧞 Commands

All commands are run from the root of the project, from a terminal:

| Command                 | Action                                           |
| :---------------------- | :----------------------------------------------- |
| `pnpm install`          | Installs dependencies                            |
| `pnpm run dev`          | Starts local dev server at `localhost:3000`      |
| `pnpm run build`        | Build your production site to `./dist/`          |
| `pnpm run preview`      | Preview your build locally, before deploying     |
| `pnpm run astro ...`    | Run CLI commands like `astro add`, `astro check` |
| `pnpm run astro --help` | Get help using the Astro CLI                     |

## 👀 Want to learn more?

Feel free to check [our documentation](https://docs.astro.build) or jump into our [Discord server](https://astro.build/chat).

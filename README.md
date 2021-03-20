# Svelte Kit vs NextJS

Comparison of major features in Svelte Kit vs NextJS.

Goals: fast, easy, convention over configuration, & batteries included.
Overwhelming choices are bad versus providing a clear path forward.

|                                                                                                 | Svelte Kit                                                                                              | NextJS                                                            | Winner    | Notes                                                                                                                                                                                                                                                                                                                                                             |
| ----------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------- | --------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| UI lib                                                                                          | Svelte                                                                                                  | React (or Preact)                                                 | SvelteKit | Svelte offers faster, more minimal DOM updates & smaller Kb client size.                                                                                                                                                                                                                                                                                          |
| Dev: Hot reload                                                                                 | 🟢                                                                                                      | 🟢                                                                | --        | I.e. Auto reload on file save.                                                                                                                                                                                                                                                                                                                                    |
| Dev: O(1) hot reload                                                                            | 🟢 Vite                                                                                                 | ❌                                                                | SvelteKit | I.e. Processes only the changed files. Fast even in big projects.                                                                                                                                                                                                                                                                                                 |
| Dev: "Fast refresh"                                                                             | 🟢                                                                                                      | 🟢                                                                | --        | I.e. UI state preserved across reloads.                                                                                                                                                                                                                                                                                                                           |
| Dev: Write modern JS                                                                            | 🟢                                                                                                      | 🟢                                                                | --        | Svelte compiler processes it. NextJS uses Babel for this.                                                                                                                                                                                                                                                                                                         |
| Dev: A11y console hints                                                                         | 🟢                                                                                                      | ❌                                                                | SvelteKit |                                                                                                                                                                                                                                                                                                                                                                   |
| Dev: Prettier                                                                                   | 🟢                                                                                                      | 🟢                                                                | --        | For `.svelte` or `.jsx` files. For SvelteKit, install `Svelte for VSCode` extension.                                                                                                                                                                                                                                                                              |
| Prod: Bundler                                                                                   | 🟢 Rollup                                                                                               | 🟢 Webpack                                                        | --        | E.g. Minify assets, etc.                                                                                                                                                                                                                                                                                                                                          |
| Prod: Auto code splitting, per route                                                            | 🟢                                                                                                      | 🟢                                                                | --        | I.e. Auto code splits JS & CSS per route & bundles appropriately.                                                                                                                                                                                                                                                                                                 |
| Prod: [HTTP2 push](https://brianli.com/cloudflare-workers-sites-http2-server-push/) of JS/CSS\* | ❌                                                                                                      | ❌                                                                | _Neither_ | I.e. Set initial page's HTML headers to push JS & CSS. Requires host support. And/or add 'link preload' to HTML head for required CSS & JS. \*Chrome deprecated this Dec 2020; may become less relevant.                                                                                                                                                          |
| Prod: Build adapters for different hosts                                                        | 🟢                                                                                                      | ❌                                                                | SvelteKit | SvelteKit provides easy portability. NextJS works best with Vercel.                                                                                                                                                                                                                                                                                               |
| Kb size: Hello World                                                                            | 0.52, 0.285 gzip, 0.18 br \*                                                                            | _?_ 204                                                           | SvelteKit | \*Mar 19 2021. <https://svelte.dev/blog/sapper-towards-the-ideal-web-app-framework>                                                                                                                                                                                                                                                                               |
| Kb size: "Real World" app                                                                       | 45.3 (~21.8 gzip)\*                                                                                     | _?_ 327 (~85.7 gzip)                                              | SvelteKit | \*Mar 13, 2021 <https://realworld.svelte.dev/>, <https://svelte.dev/blog/sapper-towards-the-ideal-web-app-framework>                                                                                                                                                                                                                                              |
| Rendering: SSR, per route                                                                       | 🟢                                                                                                      | 🟢                                                                | --        | I.e. Server-side rendered (at run time).                                                                                                                                                                                                                                                                                                                          |
| Rendering: SSG, per route                                                                       | 🟢                                                                                                      | 🟢                                                                | --        | I.e. Static (at build time).                                                                                                                                                                                                                                                                                                                                      |
| Rendering: Incremental SSG, per route                                                           | ❌                                                                                                      | 🟢                                                                | NextJS    | I.e. Static 'on demand' in production--first req dynamic then cached.                                                                                                                                                                                                                                                                                             |
| Headers: s-max-age & max-age, per route                                                         | 🟢 🟢                                                                                                   | 🟢 ❌?                                                             | --        | SvelteKit can set headers for server routes or specify max-age for client routes via load function. NextJS allows it for server routes, not client routes, but can be set via [vercel.json](https://vercel.com/docs/configuration#project/headers) if hosted on Vercel.                                                                                           |
| Routes: File-based routing                                                                      | 🟢                                                                                                      | 🟢                                                                | --        | For simplicity. Other routing utilities should be included.                                                                                                                                                                                                                                                                                                       |
| Routes: "SPA mode"                                                                              | 🟢                                                                                                      | 🟢                                                                | --        | SSR for initial page load, then client-side routing for subsequent pages.                                                                                                                                                                                                                                                                                         |
| Routes: Pre-fetch JS/CSS on link hover                                                          | 🟢                                                                                                      | 🟢 next/link                                                      | SvelteKit | Just add `sveltekit:prefetch` to a regular link. Svelte also offers a function prefetch all or some routes (via regex)--powerful! NextJS' requires using their link component; see docs. It's nicer to use regular links.                                                                                                                                         |
| Built-in: Metadata                                                                              | 🟢                                                                                                      | 🟢 next/head                                                      | --        | Place within `<svelte:head>...</svelte:head>`                                                                                                                                                                                                                                                                                                                     |
| Built-in: State management                                                                      | 🟢 svelte/store                                                                                         | ❌                                                                | SvelteKit | Ideal is one, easy, built-in way. React has many choices--Zustand is reasonable.                                                                                                                                                                                                                                                                                  |
| Built-in: Animations                                                                            | 🟢 svelte/animate                                                                                       | ❌                                                                | SvelteKit | 3rd-party options exist for React, but they're not as easy to use.                                                                                                                                                                                                                                                                                                |
| Built-in: CSS scoping                                                                           | 🟢                                                                                                      | 🟢                                                                | SvelteKit | Svelte's is automatic. NextJS' is via CSS modules or CSS in JSX (not as clean).                                                                                                                                                                                                                                                                                   |
| Web vitals reporting\*                                                                          | 🟢                                                                                                      | 🟢                                                                | NextJS    | \*Not super relevant as a framework feature anymore because easily added via analytics snippet now or via hosting platform provider. Cloudlfare Site Analytics offers web vital tracking with zero configuration; it's part of their JS snippet. [Vercel](https://vercel.com/docs/analytics) also offers it if using NextJS or NuxtJS & has a _superb_ dashboard. |
| Auth                                                                                            | ❌ ([soon?](https://github.com/sveltejs/kit/tree/master/examples/realworld.svelte.dev/src/routes/auth)) | 🟢 [NextAuth.js](https://next-auth.js.org)                        | NextJS    | NextAuth.js is defacto standard for NextJS; easy to use; email, social, &/or one-click link.                                                                                                                                                                                                                                                                      |
| Image component                                                                                 | 🟢? [svelte-image](https://svelte-image.matyunya.now.sh/)                                               | 🟢 [next/image](https://nextjs.org/docs/api-reference/next/image) | --        | Preferably optimized image generation with caching.                                                                                                                                                                                                                                                                                                               |
| Forms                                                                                           | 🟢 [Felte](https://felte.dev)                                                                           | 🟢 [Formik](https://formik.org)                                   | --        | Felte offers a nearly-native HTML5 form experience. Or [Sveltik](https://github.com/nathancahill/sveltik) is a port of Formik for React. Can use Yup for validation.                                                                                                                                                                                              |
| SWR-like data fetching                                                                          | 🟢? [svelte-query](https://github.com/SvelteStack/svelte-query)                                         | 🟢 [SWR](https://swr.vercel.app)                                  | --        | SWR is by Vercel. Easy fetch/isLoading/errors/caching.                                                                                                                                                                                                                                                                                                            |
| [Tailwind CSS](https://tailwindcss.com/) compatible                                             | 🟢                                                                                                      | 🟢                                                                | --        | Easy via github.com/svelte-add/tailwindcss. NextJS requires more steps, but [RFC](https://github.com/vercel/next.js/discussions/20030) for `npx init tailwind`                                                                                                                                                                                                    |
| [Headless UI](https://headlessui.dev/) available                                                | ❌                                                                                                      | 🚧 WIP                                                            | NextJS    | Un-styled UI components (dropdown, slider, toggle, etc) from Tailwind creators.                                                                                                                                                                                                                                                                                   |
| Docs                                                                                            | 10/10                                                                                                   | 10/10                                                             | NextJS    |                                                                                                                                                                                                                                                                                                                                                                   |

🚧 = WIP or RFC

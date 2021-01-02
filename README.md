# Svelte Kit (upcoming) vs NextJS

Comparison of major features in (the upcoming) Svelte Kit vs NextJS.

Goals: fast, easy, convention over configuration, & batteries included.
Overwhelming choices are bad versus providing a clear path forward.

|                                         | Svelte Kit              | NextJS              | Winner     | Notes                                                                             |
| --------------------------------------- | ----------------------- | ------------------- | ---------- | --------------------------------------------------------------------------------- |
| UI lib                                  | Svelte                  | React (or Preact)   | Svelte Kit | Svelte offers faster, more minimal DOM updates & smaller Kb client size.          |
| Dev: Hot reload                         | 🟢                      | 🟢                  | --         | I.e. Auto reload on file save.                                                    |
| Dev: O(1) hot reload                    | 🟢 Snowpack             | ❌                  | Svelte Kit | I.e. Processes only the changed files. Fast even in big projects.                 |
| Dev: "Fast refresh"                     | 🟢                      | 🟢                  | --         | I.e. UI state preserved across reloads.                                           |
| Dev: Write modern JS                    | 🟢                      | 🟢                  | --         | Svelte compiler processes it. NextJS uses Babel for this.                         |
| Dev: A11y console hints                 | 🟢                      | ❌                  | Svelte Kit |                                                                                   |
| Dev: Prettier                           | 🟢 \*                   | 🟢                  | --         | For `.svelte` or `.jsx` files. \*via `Svelte for VS Code` extension.               |
| Prod: Bundler                           | 🟢 Rollup               | 🟢 Webpack          | --         | E.g. Minify assets, etc.                                                          |
| Prod: Auto code splitting, per route    | 🟢                      | 🟢                  | --         | I.e. Auto code splits JS per route & bundles appropriately.                       |
| Prod: HTTP2 push of JS/CSS              | ❌                      | ❌                  | _neither_  | I.e. Set initial page's HTML headers to push JS & CSS. Requires host support.     |
| Kb size: Hello World                    | _?_ 7                   | _?_ 204             | Svelte Kit | _old sizes_, <https://svelte.dev/blog/sapper-towards-the-ideal-web-app-framework> |
| Kb size: "Real World" app               | _?_ 39.6 (11.8 gzip)    | _?_ 327 (85.7 gzip) | Svelte Kit | _old sizes_, <https://svelte.dev/blog/sapper-towards-the-ideal-web-app-framework> |
| Rendering: SSR, per route               | 🟢                      | 🟢                  | --         | I.e. Server-side rendered (at run time).                                          |
| Rendering: SSG, per route               | 🟢                      | 🟢                  | --         | I.e. Static (at build time).                                                      |
| Rendering: Incremental SSG, per route   | _?_                     | 🟢                  | NextJS     | I.e. First request dynamic, then static.                     |
| Headers: s-max-age & max-age, per route | ❌                      | ❌                  | _neither_  |                                                                                   |
| Routes: File-based routing              | 🟢                      | 🟢                  | --         | For simplicity. Other routing utilities should be included.                       |
| Routes: "SPA mode"                      | _?_                     | 🟢                  | NextJS     | I.e. After initial page load, client-side routing is used.                        |
| Routes: Pre-fetch JS/CSS on link hover  | _?_                     | 🟢 next/link        | NextJS     | NextJS' is sophisticated but requires using their link component; see docs.       |
| Built-in: Metadata                      | 🟢 svelte/head          | 🟢 next/head        | --         |                                                                                   |
| Built-in: State management              | 🟢 svelte/store         | ❌                  | Svelte Kit | Ideal is one, easy, built-in way. React has many choices--Zustand is reasonable.  |
| Built-in: Animations                    | 🟢 svelte/animate       | ❌                  | Svelte Kit | 3rd-party options exist for React, but they're not as easy to use.                |
| Built-in: CSS scoping                   | 🟢                      | 🟢                  | Svelte Kit | Svelte's is automatic. NextJS' is via CSS modules or CSS in JSX (not as clean).   |
| Built-in: Web vitals reporting          | ❌                      | 🟢                  | NextJS     | Vercel & Cloudflare 'Browser Insights' offer free analytics dashboards.           |
| Built-in: Image optimizations           | ❌                      | 🟢 next/image       | NextJS     | On-demand optimized image generation with caching.                                |
| 3rd party: Auth _IMPORTANT_             | ❌                      | 🟢 NextAuth.js      | NextJS     | NextAuth.js is defacto standard; easy; email, social, &/or magic link.     |
| 3rd party: Forms                        | 🟢 Sveltik              | 🟢 Formik           | --         | Sveltik is a port of Formik for React. Can use Yup for validation.                |
| 3rd party: SWR-like data fetching       | ❔ svelte-query (good?) | 🟢 SWR              | _?_        | SWR is by Vercel. Easy fetch/isLoading/errors/caching.                            |
| Tailwind CSS compatible                 | 🟢 \*                   | 🚧 RFC \*\*         | --         | \*via github.com/svelte-add/tailwindcss \*\*RFC for `npx init tailwind`           |
| Headless UI available                   | ❌                      | 🚧 WIP              | NextJS     | Un-styled UI components (dropdown, slider, toggle, etc) from Tailwind creators.   |
| Docs                                    | _TBD_                   | 10/10               | NextJS     |                                                                                   |

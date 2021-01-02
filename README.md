# Svelte vs NextJS

Comparison of major features in (the upcoming) Svelte Kit vs NextJS.

Goals: fast, easy, convention over configuration, & batteries included.
Overwhelming choices are bad versus providing a clear path forward.

|                                         | Svelte Kit           | NextJS              | Winner     | Notes                                                                             |
| --------------------------------------- | -------------------- | ------------------- | ---------- | --------------------------------------------------------------------------------- |
| UI lib                                  | Svelte               | React (or Preact)   | Svelte Kit | Svelte offers faster, more minimal DOM updates & smaller Kb client size.          |
| Dev: Hot reload                         | yes                  | yes                 | --         | I.e. Auto reload on file save.                                                    |
| Dev: O(1) hot reload                    | yes (Snowpack)       | _no_                | Svelte Kit | I.e. Processes only the changed files. Fast even in big projects.                 |
| Dev: "Fast refresh"                     | yes                  | yes                 | --         | I.e. UI state preserved across reloads.                                           |
| Dev: Write modern JS                    | yes                  | yes                 | --         | Svelte compiler processes it. NextJS uses Babel for this.                         |
| Dev: A11y console hints                 | yes                  | _no_                | Svelte Kit |                                                                                   |
| Dev: Prettier                           | yes\*                | yes                 | --         | For `.svelte` or `.jsx` files. \*via 'Svelte for VSCode' extension.               |
| Prod: Builder                           | Rollup               | Webpack             | --         | E.g. Minify assets, etc.                                                          |
| Prod: Auto code splitting, per route    | yes                  | yes                 | --         | I.e. Auto code splits JS per route & bundles appropriately.                       |
| Prod: HTTP2 push of JS/CSS              | _no_                 | _no_                | _Neither_  | I.e. Sets initial page's HTML headers to push JS/CSS. Requires host support.      |
| Kb size: Hello World                    | _?_ 7                | _?_ 204             | Svelte Kit | _old sizes_, <https://svelte.dev/blog/sapper-towards-the-ideal-web-app-framework> |
| Kb size: "Real World" app               | _?_ 39.6 (11.8 gzip) | _?_ 327 (85.7 gzip) | Svelte Kit | _old sizes_, <https://svelte.dev/blog/sapper-towards-the-ideal-web-app-framework> |
| Render: SSR, per route                  | yes                  | yes                 | --         | I.e. Server-side rendered (at run time).                                          |
| Render: SSG, per route                  | yes                  | yes                 | --         | I.e. Static (at build time).                                                      |
| Render: Incremental SSG, per route      | _?_                  | yes                 | NextJS     | I.e. Static 'on demand' in prod--1st req dynamic then cached.                     |
| Headers: s-max-age & max-age, per route | _no_                 | _no_                | _Neither_  |                                                                                   |
| Routes: File-based routing              | yes                  | yes                 | --         | For simplicity. Other routing utilities should be included.                       |
| Routes: "SPA mode"                      | _?_                  | yes                 | NextJS     | I.e. After initial page load, client-side routing is used.                        |
| Routes: Pre-fetch JS/CSS on link hover  | _?_                  | yes (next/link)     | NextJS     | NextJS' is sophisticated but requires using their link component; see docs.       |
| Built-in: Metadata                      | yes (svelte/head)    | yes (next/head)     | --         |                                                                                   |
| Built-in: State management              | yes (svelte/store)   | _no_                | Svelte Kit | Ideal is one, easy, built-in way. React has many choices--Zustand is reasonable.  |
| Built-in: Animations                    | yes (svelte/animate) | _no_                | Svelte Kit | 3rd-party options exist for React, but they're not as easy to use.                |
| Built-in: CSS scoping                   | yes                  | yes                 | Svelte Kit | Svelte's is automatic. NextJS' is via CSS modules or CSS in JSX (not as clean).   |
| Built-in: Web vitals reporting          | _no_                 | yes                 | NextJS     | Vercel & Cloudflare 'Browser Insights' offer free analytics dashboards.           |
| Built-in: Image optimizations           | _no_                 | yes (next/image)    | NextJS     | On-demand optimized image generation with caching.                                |
| 3rd party: Auth _IMPORTANT_             | _no_                 | NextAuth.js         | NextJS     | NextAuth.js is defacto standard; easy to use; email, social, &/or magic link.     |
| 3rd party: Forms                        | Sveltik              | Formik              | --         | Sveltik is a port of Formik for React. Can use Yup for validation.                |
| 3rd party: SWR-like data fetching       | svelte-query (good?) | SWR                 | _?_        | SWR is by Vercel. Easy fetch/isLoading/errors/caching. \*See link below           |
| Tailwind CSS compatible                 | yes\*                | yes\*\* (WIP)       | --         | \*via github.com/svelte-add/tailwindcss \*\*RFC for `npx init tailwind`           |
| Headless UI available                   | _no_                 | _no_ (WIP)          | NextJS     | Un-styled UI components (dropdown, slider, toggle, etc) from Tailwind creators.   |
| Docs                                    | _TBD_                | 10/10               | NextJS     |                                                                                   |

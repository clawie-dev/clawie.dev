# clawie.dev

Landing page + documentation site for **Clawie, the Autonomous Software Agency Framework**.

Next.js (App Router) + React, frontend-only, static-export friendly. Pulls content from sibling repos at build time:

- [`clawie-dev/docs`](https://github.com/clawie-dev/docs) → prose documentation
- [`clawie-dev/specs`](https://github.com/clawie-dev/specs) → formal specifications

Deployed to Cloudflare Pages.

## Build pipeline (planned)

```
build:
  1. git clone (shallow) docs/ and specs/ into content/
  2. transform markdown → MDX with custom components
  3. next build → static export
  4. wrangler pages deploy
```

## Status

Bootstrap pending. See [`clawie-dev/specs`](https://github.com/clawie-dev/specs) for the platform spec context.

## License

MIT — see [LICENSE](LICENSE).

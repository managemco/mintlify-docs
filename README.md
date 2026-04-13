# Documentation

This repository powers the documentation found over at https://docs.managem.co.uk. It is built using [Mintlify](https://www.mintlify.com) and the source files are written in Markdown and MDX.

> The most important file is [docs.json](./docs.json), which configures the structure of the documentation, including the sidebar navigation and links to OpenAPI specs for interactive API reference.

## Development

### Prerequisites

- Node.js **24 or higher** (see [.nvmrc](./.nvmrc)). If you use [nvm](https://github.com/nvm-sh/nvm), run `nvm use` from the repo root.
- `npm` (bundled with Node).

### Run the docs site locally

From the repo root:

```bash
npm install
npm run dev
```

`npm run dev` starts the Mintlify development server via [portless](https://github.com/egoist/portless), which provisions a trusted local HTTPS hostname. The documentation will be available at:

> https://docs.managem.localhost:4562

The server watches for changes and refreshes your browser automatically.

> **Note:** The underlying Mintlify CLI also supports a simpler `mint dev` on `http://localhost:3000`. We prefer `npm run dev` because it matches the production hostname and HTTPS behaviour of [docs.managem.co.uk](https://docs.managem.co.uk). See [development.mdx](./development.mdx) for the upstream Mintlify workflow.

## Prose linting with Vale

Use Vale to lint Markdown and MDX prose across the docs.

### Install Vale

macOS (Homebrew):

```bash
brew install vale
```

Linux (Snap):

```bash
sudo snap install vale
```

If your Linux distro does not use Snap, install Vale from the official releases listed at https://vale.sh/docs/vale-cli/installation.

### Run prose checks

Install project dependencies first (this includes `mdx2vast`, which Vale uses to parse Mintlify `.mdx` files):

```bash
npm install
```

Run Vale:

```bash
npm run check:prose
```

### API Changes

If you need to develop against local alterations to the Managem API, temporarily update the `"openapi"` property in [docs.json](./docs.json) to point at a local OpenAPI spec URL served by your API (for example `https://api.managem.localhost:4562/doc`, matching however your local API is exposed). Remember to revert before opening a PR.

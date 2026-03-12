# Documentation

This repository powers the documentation found over at https://docs.managem.co.uk. It is built using [Mintlify](https://www.mintlify.com) and the source files are written in Markdown and MDX.

> The most important file is [docs.json](./docs.json), which configures the structure of the documentation, including the sidebar navigation and links to OpenAPI specs for interactive API reference.

## Development

When developing the documentation locally, run `npm run dev` to start the Mintlify development server. This will automatically watch for changes in the repository and refresh the documentation in your browser.

The documentation will be available at: https://docs.managem.localhost:1355

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

If you need to develop against local alterations to the Managem API, you need to temporarily update the `"openapi"` property in `docs.json`, to point at the local OpenAPI spec file:

> https://api.managem.localhost:1355/doc

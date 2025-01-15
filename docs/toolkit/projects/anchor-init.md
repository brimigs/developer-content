---
title: Basic Anchor Smart Contracts
sidebarSortOrder: 2
sidebarLabel: Basic Anchor
---

> This is a beta version of the [Solana Toolkit](/docs/toolkit/index.md), and is
> still a WIP. Please post all feedback as a GitHub issue
> [here](https://github.com/solana-foundation/developer-content/issues/new?title=%5Btoolkit%5D%20).

```shell
anchor init <project_name>
```

## Overview

This initializes a simplistic workspace set up for Anchor smart contract
development, with the following structure:

- `Anchor.toml`: Anchor configuration file.
- `Cargo.toml`: Rust workspace configuration file.
- `package.json`: JavaScript dependencies file.
- `programs/`: Directory for Solana program crates.
- `app/`: Directory for your application frontend.
- `tests/`: Directory for JavaScript integration tests.
- `migrations/deploy.js`: Deploy script.

The Anchor framework abstracts away many complexities enabling fast program
development.

## Build and Test

To test out this project before making any modifications, just build and test:

```shell
anchor build
```

```shell
anchor test
```

To start writing your own Anchor smart contract, navigate to
`programs/src/lib.rs`.

## File Structure Template

For more complex programs, using a more structured project template would be the
best practice. This can be generated with:

```shell
anchor init --template multiple
```

Which creates the following layout inside of `programs/src`:

```shell
├── constants.rs
├── error.rs
├── instructions
│   ├── initialize.rs
│   └── mod.rs
├── lib.rs
└── state
    └── mod.rs
```

For project file structure best practices, review this
[document](/docs/toolkit/projects/project-layout.md).

## Additional Resources

- [Anchor book](https://www.anchor-lang.com/)
- [Getting Started with Anchor](/docs/programs/anchor/index.md)
- [Program Examples](https://github.com/solana-developers/program-examples)
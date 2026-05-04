# bitchain-studio

A standalone desktop and mobile GUI for creating and managing [bitchain](https://github.com/dlockamy/bitchain) bundles.

`bitchain-studio` puts a visual interface over the `bitchain` CLI — browse your files, configure block storage backends, inspect manifests, and rebuild assets without touching the command line. Designed for artists, designers, and content creators who need reliable binary asset versioning without learning Rust or S3 tooling.

## Status

🚧 **In development** — see [KAN-81](https://fairmerce.atlassian.net/browse/KAN-81) for planning status.

## Relationship to bitchain

| Tool | Audience | Interface |
|---|---|---|
| [bitchain](https://github.com/dlockamy/bitchain) | Developers | CLI |
| **bitchain-studio** | Everyone | Desktop / Mobile |
| [refraction](https://github.com/dlockamy/refraction) | Enterprise teams | Self-hosted SaaS |

## Planned Features

- Visual file browser for ingesting files and directories into bitchain bundles
- Storage backend configuration (S3, HTTP, local) via a guided setup UI
- Manifest inspector — browse blocks, URIs, and hashes in a structured view
- One-click rebuild from any manifest file
- Bundle history and diff view
- Cross-platform: macOS, Windows, Linux, iOS, Android

## Development

See [bitchain](https://github.com/dlockamy/bitchain) for the core CLI that powers this application.

## License

TBD

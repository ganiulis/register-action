# Register Action

## Requirements

- A `Dockerfile` with a `production` build target at the root of the project.

## Example

```yaml
name: Registry

on:
  workflow_dispatch:

jobs:
  register:
    runs-on: ubuntu-latest
    permissions:
      contents: read
      packages: write
    steps:
      - uses: ganiulis/register-action@v0.1.0
        with:
          image: php
          password: ${{ github.token }}
          version: 2024.05.25.${{ github.sha }}
```

## Notes

1. Uses `ghcr.io` as the host registry by default.
2. Builds for the `linux/amd64` platform by default.
3. Docker [provenance attestations](https://docs.docker.com/build/attestations/slsa-provenance/) are disabled.

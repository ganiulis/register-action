# Register Action

## Requirements

- A `Dockerfile`.
- A build target (either a `production` default or specified with `build-target`).

## Example

```yaml
name: Register

on:
  workflow_dispatch:

jobs:
  register:
    runs-on: ubuntu-latest
    permissions:
      contents: read
      packages: write
    steps:
      - uses: ganiulis/register-action@0.1.0
        with:
          image: my-api
          password: ${{ github.token }}
          version: ${{ github.sha }}
```

## Notes

1. Uses `ghcr.io` as the host registry by default.
2. Builds for the `linux/amd64` platform by default.
3. Docker [provenance attestations](https://docs.docker.com/build/attestations/slsa-provenance/) are disabled.

# Hippocampus model artifacts

This repository hosts the versioned retrieval-model inputs used by the
[Hippocampus build pipeline](https://github.com/amyjainberkeley/hippocampus).
Application source, issues and qualification records remain in that repository.
This is a model dependency, not an app installer or a public-readiness claim.

## Release 0.2.0

The archive contains the compiled FP16 Core ML derivative of
[Snowflake Arctic Embed S](https://huggingface.co/Snowflake/snowflake-arctic-embed-s/tree/e596f507467533e48a2e17c007f0e1dacc837b33),
pinned to upstream revision `e596f507467533e48a2e17c007f0e1dacc837b33`.
It is the required semantic-retrieval model; it is separate from screenshot OCR.
The model targets macOS 14 or later, has fixed 128-token inputs and produces
a 384-dimensional normalized embedding.

The model is distributed under Apache-2.0. This repository and the model archive
include the complete license and a notice describing the Core ML conversion.
See [NOTICE](NOTICE) and [LICENSE](LICENSE).

Download `release-models-0.2.0.tar.gz` and its SHA-256 sidecar from the versioned
release. The archive has seven files: five compiled-model/contract files and
two attribution files. [The receipt](model-archive-receipt.json) records every
file's size and digest. It contains no app binary, personal memory, credentials,
Qwen or NER models.

Archive SHA-256:

`e0d9a98ef6cb793aa539b1719a4546c2de16f9c445c60fe846829928daa5a718`

To reconstruct it, use the application repository's existing verifier:

```sh
scripts/prepare-release-models.sh \
  --archive /path/to/release-models-0.2.0.tar.gz \
  --sha256 e0d9a98ef6cb793aa539b1719a4546c2de16f9c445c60fe846829928daa5a718 \
  --output /path/to/new-models-directory
```

The verifier checks the archive hash, rejects links/path traversal, validates
the shipping model contract and refuses to overwrite existing model directories.
The archive is normalized to sorted paths, zero timestamps, root ownership and
fixed permissions. GitHub release immutability is enabled before publication;
future changes require a new version.

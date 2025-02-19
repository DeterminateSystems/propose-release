# prepare-release

Internal tooling for coordinating releases.
Example:

```yml
on:
  workflow_dispatch:
    inputs:
      reference-id:
        type: string
        required: true
      version:
        type: string
        required: true

concurrency:
  group: ${{ github.workflow }}
  cancel-in-progress: true

jobs:
  prepare-release:
    uses: DeterminateSystems/prepare-release/.github/workflows/workflow.yml@main
    permissions:
      id-token: "write"
      contents: "write"
      pull-requests: write
    with:
      reference-id: ${{ inputs.reference-id }}
      version: ${{ inputs.version }}
```

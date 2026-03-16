# docker-imageexists-action

Checks if given Docker image exists.

Ensure that Docker is installed prior to this action.

## Usage


```yml
name: Check if image exists
on:
  workflow_dispatch:

jobs:
  retag:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v6

      - name: Check if image exists
        id: image_check
        uses: mspanc/docker-imageexists-action@v1
        with:
          source: my-image:latest

      - name: Build image
        if: steps.image_check.outputs.exists != 'true'
        run: |
          echo "Build here"          
```
## Designer Workflow

1. A designer updates variables in Figma.
2. Using the [Tokens Studio Figma Plugin](https://tokens.studio/):
   - A designer imports the updated Figma variables.
   - A designer pushes the updated tokens (W3C compliant design tokens) to the `develop` branch.
   - A designer opens a pull request to merge `develop` into `main`.

## Developer Workflow

- when a pull request is opened, a [github action is triggered](https://github.com/MeowWolf/figma-tokens/blob/main/.github/workflows/build.yml) which reads the updated `tokens.json` file and generates our updated styles using [style dictionary](https://amzn.github.io/style-dictionary/#/)
- a developer(s) reviews the pull request and approves/requests changes.
- upon approval, a developer adds the "version bump" label to the pull request.
- adding the "version bump" label [triggers a github action](https://github.com/MeowWolf/figma-tokens/blob/main/.github/workflows/bump.yml) which issues a git release tag and bumps the `package.json` version.
- a developer creates a release from the latest tag in github.
- Creating a release from the tag in github [triggers another github action](https://github.com/MeowWolf/figma-tokens/blob/main/.github/workflows/publish.yml) which publishes a release to NPM.
- a developer updates all applications that use `figma-tokens` as a dependency.

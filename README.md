1) sync figma variables using figma tokens (https://tokens.studio/) github integration
2) When figma tokens are updated through the figma tokens plugin push changes to `develop` and open a pull request.
3) When a pull request is opened against `main` the `build.yml` GH Action runs which bumps the version (package.json), issues a tag, and builds the updated css variables using style-dictionary.
4) To publish to npm, simply merge the pull request to main and create a release from the latest tag.

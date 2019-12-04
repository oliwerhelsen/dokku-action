# Dokku for GitHub Actions

Deploy a master branch to your Dokku server.

This action will deploy the master brunch to your Dokku server via SSH.

## Usage

To use the action simply add the following lines to your `.github/workflows/main.yml`

```
name: CD

on:
  push:
    branches:
      - master

jobs:
  build:

    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v1
    - name: Dokku deploy
      uses: vitalyliber/dokku-github-action@master
      env:
        PRIVATE_KEY: ${{ secrets.PRIVATE_KEY }}
        PUBLIC_KEY: ${{ secrets.PUBLIC_KEY }}
        HOST: casply.com
        PROJECT: kawaii
```

### Required Secrets

You'll need to provide some secrets to use the action.

- **PRIVATE_KEY**: Your SSH private key.
- **PUBLIC_KEY**: Your SSH public key.

### Required Environments

You'll need to provide some env to use the action.

- **HOST**: The host the action will SSH to run the git push command. ie, `your.site.com`.
- **PROJECT**: The project is Dokku project name.
- **BRANCH**: Repository branch that should be used for deploy, `master` is set by default.
- **PORT**: Port of the sshd listen to, `22` is set by default.

## License

The Dockerfile and associated scripts and documentation in this project are released under the [MIT License](LICENSE).

This repository explains how to run the [JValue Open Data Service](https://github.com/jvalue/open-data-service) without building it yourself.

It uses [GitHub Packages](https://docs.github.com/en/free-pro-team@latest/packages) to achieve this.

# Usage of the ODS

## Setting up

### Requirements:
- GitHub account
- Docker
- Docker-Compose

### Login into Github Packages

Source: [Official Github Package Documentation](https://docs.github.com/en/free-pro-team@latest/packages/managing-container-images-with-github-container-registry/pushing-and-pulling-docker-images#authenticating-to-github-container-registry)

You will need a Personal Access Token (PAT) to download the packages from the registry automatically.

You can create it in the [GitHub settings](https://github.com/settings/tokens). You will need a token with the scope `read:packages` enabled (nothing else is required).

Use the token and your github username to log into the github docker registry e.g. like so:

```bash
$ export CR_PAT=YOUR_TOKEN
$ echo $CR_PAT | docker login https://docker.pkg.github.com -u USERNAME --password-stdin
> Login Succeeded
```

### Pull images
Use `docker-compose pull` to fetch the newest versions of all used images from GitHub Packages. You can rerun this command again to get updates, or specify a specific service to only pull that image (e.g. `docker-compose pull adapter`).

### Start the ODS

You can use `docker-compose up` to start the ODS. Use the option `-d` if you want to start it in the background and reuse the terminal window.


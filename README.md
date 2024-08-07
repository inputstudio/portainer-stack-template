# Portainer stack deployment template

This is a template for deploying Portainer stacks with GitHub Actions.

**Note:** Using [Portainer webhooks](https://docs.portainer.io/user/docker/stacks/webhooks) requires [Portainer Business Edition](https://www.portainer.io/features). You can get a free license [here](https://www.portainer.io/get-a-license).

## Features

- 🐋 GitHub Actions workflow to build and push the image to whatever registry you want (defaults to `ghcr.io`)
- 🪝 Webhook to automatically update the stack on Portainer

## Usage

1. Download the `deploy.yml` and move it to the `.github/workflows` folder:

```bash
curl -LJO https://raw.githubusercontent.com/inputstudio/portainer-stack-template/main/.github/workflows/deploy.yml
```

If you don't have `curl` installed, you can open the link above and copy the content to a new file named `deploy.yml` in the `.github/workflows` folder.

2. Edit `deploy.yml` replacing `ghcr.io/inputstudio/hello-world` with your image name.

3. Create your `Dockerfile` and `compose.yml` or use [docker init](https://docs.docker.com/reference/cli/docker/init/):

```bash
docker init
```

4. (optional) If you want to use environment variables in your stack, add the following to your `compose.yml`:

```yaml
services:
  my-service:
    env_file:
      - stack.env # This file contains all the environment variables set in the stack editor
```

5. [Add a stack on Portainer](https://docs.portainer.io/user/docker/stacks/add) and [enable GitOps webhook](https://docs.portainer.io/user/docker/stacks/webhooks).
6. Add the webhook URL to your GitHub repo secrets as `PORTAINER_STACK_WEBHOOK`.
7. Done 🎉

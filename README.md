# Portainer stack deployment template

This is a template for deploying Portainer stacks with GitHub Actions.

**Note:** Using [Portainer webhooks](https://docs.portainer.io/user/docker/stacks/webhooks) requires [Portainer Business Edition](https://www.portainer.io/features). You can get a free license [here](https://www.portainer.io/get-a-license).

## Features

- 🐋 GitHub Actions workflow to build and push the image to whatever registry you want (defaults to `ghcr.io`)
- 🪝 Webhook to automatically update the stack on Portainer

## Usage

1. Install [degit](https://www.npmjs.com/package/degit):

```bash
npm install -g degit
```

2. Clone this template to your project folder:

```bash
cd your-project-folder
degit github:inputstudio/portainer-stack-template
```

3. Edit `.github/workflows/deploy.yml` replacing `ghcr.io/inputstudio/hello-world` with your image name.

4. Create your `Dockerfile` and `compose.yml` or use [docker init](https://docs.docker.com/reference/cli/docker/init/):

```bash
docker init
```

5. (optional) If you want to use environment variables in your stack, add the following to your `compose.yml`:

```yaml
services:
  my-service:
    env_file:
      - stack.env # This file contains all the environment variables set in the stack editor
```

6. Add a stack on Portainer. Learn how to do it [here](https://docs.portainer.io/user/docker/stacks/add).
7. Enable the webhook on the stack. Learn how to do it [here](https://docs.portainer.io/user/docker/stacks/webhooks).
8. Add the webhook URL to your GitHub repo secrets as `PORTAINER_STACK_WEBHOOK`.
9. Done 🎉

# Portainer stack deployment template

This is a template for deploying Portainer stacks.

## Features

- 🐋 GitHub Actions workflow to build and push the image to whatever registry you want (defaults to `ghcr.io`)
- 🪝 Webhook to automatically update the stack on Portainer

## Usage

1. Use degit to clone this repo and remove the git history:

```bash
npm install -g degit # if you don't have degit installed
cd your-project-folder
degit github:inputstudio/portainer-stack-template
```

2. Make your changes to the `compose.yaml` and `Dockerfile` file and commit them to your repo.
3. Add a stack on Portainer. Learn how to do it [here](https://docs.portainer.io/user/docker/stacks/add).
4. Enable the webhook on the stack. Learn how to do it [here](https://docs.portainer.io/user/docker/stacks/webhooks).
5. Add the webhook URL to your GitHub repo secrets as `PORTAINER_STACK_WEBHOOK`.
6. Enjoy!

A Docker image build will be triggered every time you push to the `main` branch. The image will be tagged with the commit hash and pushed to `ghcr.io` (you can change that). The stack will be updated automatically via webhook.

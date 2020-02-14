# Akeneo Connector for SFCC help center
This repository holds the sources of the Akeneo Connector for SFCC help center, made by hand with love.

### Requirement

Install [Docker Engine](https://docs.docker.com/engine/installation/)

### Build with docker

```bash
make build
```

This is only building the documentation. The documentation is not available with this command, as it does not launch the HTTP server. 

### Build and launch HTTP server with docker

```bash
make watch
```

The help center website is then available on `http://localhost:8000/sfcc/v19/`.
Files located in the content and src directories are watched for changes, so when developing or writing new articles you do not need to launch any other task.

## Deployment of master version

### With Circle CI (recommended)

Once you merge a PR into the `master` branch, it is automatically deployed on the staging server. In order to deploy it in production, please follow these steps:

- Check the staging environment if everything is ok to be deployed in production
- Open [the list of merged PR in master branch](https://circleci.com/gh/akeneo/workflows/sfcc-helpcenter/tree/master) in Circle CI. You have to be connected with your Github account.
- Click on the first row which should be "On hold"

![List of merged PR in master](.circleci/list_workflows.jpg)

- Click on the box "approve_to_deploy_in_production" and approve. It will launch the deployment in production.

![List of jobs in a workflow](.circleci/list_jobs.jpg)

- It's deployed in production in 1 minute!

### Local deployment (not recommended)

Your public SSH key should be deployed on the server (see Ansible configuration). It is strongly recommended to release with the CI process though.

```bash
HOSTNAME=xxx PORT=xxx make deploy
```

HOSTNAME is the server to deploy the documentation on.
PORT is the SSH port to connect to the server.

To know the production and staging environments of sfcc-helpcenter, please read the [inventory](https://github.com/akeneo/ansible/blob/master/inventories/core.inventory).

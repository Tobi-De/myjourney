# myjourney

[![falco](https://img.shields.io/badge/built%20with-falco-success)](https://github.com/Tobi-De/falco)
[![Ruff](https://img.shields.io/endpoint?url=https://raw.githubusercontent.com/astral-sh/ruff/main/assets/badge/v2.json)](https://github.com/astral-sh/ruff)
[![linting: pylint](https://img.shields.io/badge/linting-pylint-yellowgreen)](https://github.com/PyCQA/pylint)
[![Hatch project](https://img.shields.io/badge/%F0%9F%A5%9A-Hatch-4051b5.svg)](https://github.com/pypa/hatch)


## Deploy

### VPS

### Ansible

### Caprover

- If you use github, instead of entering your password directly into the ``password`` field, you can use a `personal access token <https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token>`__, which is a more secure option.

- Checkout `caprover automatic deploy <https://caprover.com/docs/deployment-methods.html#automatic-deploy-using-github-bitbucket-and-etc>`__ to automate the deployment of your applications.

   If you have generate a template with the ``falco`` cli or you have a dockerfile at your disposal, the only config you need in your projec to run caprover is this

```text
    {
       "schemaVersion": 2,
       "dockerfilePath": "./deploy/Dockerfile" # the path to your dockerfile
    }
```

open ssh console

```bash
docker exec -it $(docker ps --filter name=myjourney -q) /bin/sh
```

## Prerequisites

- `Python 3.11+`
- `hatch 1.9.1+`
- `Postgresql 13+`

## Development

### Create a new virtual environment

```shell
hatch shell
```

### Install pre-commit

```shell
git init && pre-commit install
```

Ensure that the Python version specified in your `.pre-commit-config.yaml` file aligns with the Python version installed on your system.

### Create a `.env` file

```shell
falco sync-dotenv
```

### Apply migrations

```shell
hatch run migrate
```

### Create a superuser

Fill the `SUPERUSER_EMAIL` and `SUPERUSER_PASSWORD` in your `.env` file and run:

```shell
falco make-superuser
```

### Run the django development server

```shell
hatch run runserver
# if you've aliased `hatch run` to `hr``
hr runserver
# if you've added falco-cli as a dependency to your project
falco work
```

# gitea-runner-docker-compose

Containerized gitea runner for self hosted gitea instance

## Setup instructions

This guide assumes that you already have a self hosted gitea server. You'll first have to have a VM with docker engine installed. I used ubuntu. Follow the instructions at https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository

### Clone the repo
git clone this repo

```
git clone https://github.com/brootware/gitea-runner-docker-compose.git
cd gitea-runner-docker-compose
```

### Set environment variables

Rename `[sample.env](sample.env)` to `.env` and replace the values with yours

```
INSTANCE_URL=https://gitea.fqdn
REGISTRATION_TOKEN=[git.fqdn>user>settings>actions>runners>createnewrunner]
RUNNER_NAME=namehere
RUNNER_LABELS=namehere
```

### Download gitea runner binary and generate the latest config.yaml file

Download gitea runner binary from https://gitea.com/gitea/act_runner/releases and rename it to `act_runner`

```
wget [URL HERE]
mv binaryfile act_runner
chmod +x act_runner
```

Generate config.yaml

```
./act_runner generate-config > config.yaml
```

### Run

```
docker compose up -d
```
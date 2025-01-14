---
title: "Installation"
description: "Use various installation methods."
lead: ""
images: []
menu:
  docs:
    parent: "get-started"
weight: 1200
toc: true
---

## binary

Krab binary can be downloaded from [GitHub](https://github.com/ohkrab/krab/releases). Other methods are listed below.

## asdf

Krab provides [asdf plugin](https://github.com/ohkrab/asdf-krab) (make sure you have asdf updated):

```sh
asdf plugin add krab
```

Install desired version:

```sh
asdf install krab 0.7.0
```

Set it to your project:

```sh
asdf local krab 0.7.0
```

## docker

Docker images can be found at [Docker hub](https://hub.docker.com/orgs/ohkrab/repositories).

To start a docker container a `DATABASE_URL` environment variable must be provided.
By default "krab" reads configuration from `/etc/krab` that must be mounted as a volume,
the path can be changed by `KRAB_DIR` environment variable.

Pull the docker image:
```sh
docker pull ohkrab/krab:nightly
```

Example:

```sh
docker run --rm                          \  # remove container after command execution
        -e DATABASE_URL="..."            \  # provide connection string
        -v ${HOME}/project1:/etc/krab:ro \  # mount configuration volume
        ohkrab/krab:nightly version    # run `version` command from `qbart/krab:latest`
```

one-liner:

```sh
docker run --rm -e DATABASE_URL="..." -v ${HOME}/project1:/etc/krab:ro ohkrab/krab:nightly --version
```


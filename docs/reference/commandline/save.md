---
title: "save"
description: "The save command description and usage"
keywords: "tarred, repository, backup"
---

# save

```markdown
Usage:  docker save [OPTIONS] IMAGE [IMAGE...]

Save one or more images to a tar archive (streamed to STDOUT by default)

Aliases:
  docker image save, docker save

Options:
      --help            Print usage
  -o, --output string   Write to a file, instead of STDOUT
```

## Description

Produces a tarred repository to the standard output stream.
Contains all parent layers, and all tags + versions, or specified `repo:tag`, for
each argument provided.

## Examples

### Create a backup that can then be used with `docker load`.

```console
$ docker save busybox > busybox.tar

$ ls -sh busybox.tar

2.7M busybox.tar

$ docker save --output busybox.tar busybox

$ ls -sh busybox.tar

2.7M busybox.tar

$ docker save -o fedora-all.tar fedora

$ docker save -o fedora-latest.tar fedora:latest
```

### Save an image to a tar.gz file using gzip

You can use gzip to save the image file and make the backup smaller.

```console
$ docker save myimage:latest | gzip > myimage_latest.tar.gz
```

### Cherry-pick particular tags

You can even cherry-pick particular tags of an image repository.

```console
$ docker save -o ubuntu.tar ubuntu:lucid ubuntu:saucy
```

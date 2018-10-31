Inside directory with `APKBUILD` file use to run `abuild -r` previously use `apk update` to fetch fresh packages

You could use following `Makefile` to inside directory with aports https://github.com/alpinelinux/aports

```
.PHONY: run

all: run

IMAGE := skilldlabs/aports-build:edge

run:
    docker run --rm -it -v $(shell pwd):/mnt --network host $(IMAGE) ash
```

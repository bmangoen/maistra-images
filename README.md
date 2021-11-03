# Issues for this repository are disabled

Issues for this repository are tracked in Red Hat Jira. Please head to <https://issues.redhat.com/browse/MAISTRA> in order to browse or open an issue.

# Dockerfiles for CentOS based images of Istio

Images are on [Quay.io](https://quay.io/organization/maistra).

## Building
In order to build them locally, you can make use of the helper script `create-images.sh`, passing the desired tag:
```sh
./create-images.sh -t my-tag -b
# -t is the tag, -b stands for "build"
```
This will build all images locally with the name maistra/*COMPONENT*:my-tag.

If you don't want to follow this naming, you can always build them individually, for example:
```sh
docker build -t my-pilot:my-tag -f Dockerfile.pilot .
```

## Helper scripts
### update-artifacts.sh
Before creating images you probably want to grab the latest artifacts from their repos. `update-artifacts.sh` will do that for you. Just run it and newer artifacts will be downloaded into the `artifacts` dir, ready to be consumed by the `Dockerfile`s.

### create-images.sh
`create-images.sh` is able to do more than just, say, creating images. It supports removal (untagging), building and pushing of images.

Example: if you want to build local images (`-b`) but want to remove (untag) previously existing local images (`-d`) first, and after building, you want to push (`-p`) them, run:
```sh
./create-images.sh -t my-tag -b -d -p
```
Run `./create-images.sh` to see all the options.

## Versions

Versions are tracked in a branch for each release name. For example, the maistra-2.1 branch tracks the 2.1 release.

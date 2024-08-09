# Software Update

## TL'DR

```bash
# In case you want to test a release candidate of `sconectl`, you can change the repo and the VERSION
export SCONECTL_REPO=registry.scontain.com/cicd # default is registry.scontain.com/sconectl
export VERSION=5.8.0  # default version is "latest".
export CAS="cas" # set the name of the CAS instance that we should used; default is "cas"
export CAS_NAMESPACE="scone-system" # set the Kubernetes namespace of the CAS instance that we should used; default is "default"

# if you want to use the latest stable release, ensure that these variables are not set:
unset SCONECTL_REPO
unset VERSION
# cleanup the last state
rm -rf release.sh target
# define REPO to which you are # define REPO to which you are permitted to push container images
REPO="<YOUR-REPO>"
# execute all steps of this tutorial
./run.sh -i "$REPO" --release secure-doc-management -v
```

## Introduction

In this tutorial, we show how to perform software updates of confidential applications using two versions of the program.

## Cleanup

Erase old build files and use pre-release images (if you cannot find the requested version of the images on the default git repo)

```bash
rm -rf release.sh target

export SCONECTL_REPO=registry.scontain.com/cicd
```

## First Version

Generate the first version:

```bash
# set REPO to a registry where you can push generated container images. For example, REPO could be defined as follows:
# export REPO=registry.scontain.com/cicd
export REPO=...
./run.sh -i $REPO --release software-update-tutorial
```

Install this version:

```bash
helm install software-update-tutorial ./target/helm
```

## Next Versions

Just run it again to create the second version:

```bash
./run.sh -i $REPO --release software-update-tutorial
```

If you run it again, it will generate the next version. We only defined two versions. Hence, after the second version, we switch back to the first version (instead of a third version).

```bash
./run.sh -i $REPO --release software-update-tutorial
```

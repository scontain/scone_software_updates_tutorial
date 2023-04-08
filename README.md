# Software Update

In this tutorial, we show how to perform software updates of confidential applications using two versions of the program.

## Cleanup

Erase old build files:

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

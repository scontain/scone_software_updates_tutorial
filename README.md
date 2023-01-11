# Software Update

In this tutorial, we show how to perform software updates of confidential applications using two versions of the program.

## Cleanup

```bash
rm -rf release.sh target
```

## First Version

```bash
./run.sh -i registry.scontain.com/cicd --release software-update-tutorial
```

```bash
helm install software-update-tutorial ./target/helm
```

## Next Versions

Just run it again:

```bash
./run.sh -i registry.scontain.com/cicd --release software-update-tutorial
```


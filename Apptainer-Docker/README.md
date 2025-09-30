## Using Apptainer on BMRC 

Apptainer on BMRC doesn't require any module loads as it is installed within the operating system. i.e. You can call `apptainer` command from any login or Slurm session without loading a module 

By default, Apptainer will attempt to use your home directory for all operations by creating a hidden directory *~/.apptainer*. Since home directories are limited to 10GB, we recommend redirecting these operations to the another file system. This can be achieved by setting the following environment variables before running `apptainer` command. 

```bash
mkdir -p /well/dendrou/users/$USER/work/apptainer-cache
export APPTAINER_CACHEDIR="/well/dendrou/users/$USER/work/apptainer-cache"
export APPTAINER_TMPDIR=${APPTAINER_CACHEDIR}
```

>**Add those environment variables to your *~/.bashrc* for future use**
>
>We recommend adding those environment variables to your *~/.bashrc*.
>
>
>echo 'export APPTAINER_CACHEDIR="/well/dendrou/users/$USER/work/apptainer-cache"' >> ~/.bashrc
>echo 'export APPTAINER_TMPDIR="/well/dendrou/users/$USER/work/apptainer-cache"' >> ~/.bashrc

## Pull pre-built docker container as apptainer

```bash
apptainer pull panpipes-1.2.0.aif docker://dinindusenanayake/panpipes:1.2.0
```

## Build apptainer image on BMRC as fakeroot


```bash
apptainer build --force --fakeroot panpipes-1.2.0.aif panpipes_1.2.0.def
```
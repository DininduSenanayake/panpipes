## Pull pre-built docker container as apptainer

```bash
apptainer pull panpipes-1.2.0.aif docker://dinindusenanayake/panpipes:1.2.0
```

## Build apptainer image on BMRC as fakeroot

* Make sure to set `APPTAINER_CACHEDIR` and `APPTAINER_TMPDIR` variables to a path away from home ( defailt is `$HOME`). .i.e Apptainer caching can accumulate few GBs or tens of GBs very quickly. Therefore, default `$HOME` is not suitable 

```bash
apptainer build --force --fakeroot panpipes-1.2.0.aif panpipes_1.2.0.def
```
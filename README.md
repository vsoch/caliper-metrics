# Caliper Metrics

This is a repository of extracted metrics data using [caliper](https://github.com/vsoch/caliper). 
Both the library and data repository are under development.

## Automated Updates

To update automatically, we use the [caliper update](https://caliper-python.readthedocs.io/en/latest/getting_started/user-guide.html#checking-and-updating-metrics)
functionality to do updates, which reads from [caliper.yaml](caliper.yaml) to get the listing of libraries:

```bash
$ caliper update
```

which you can also use to just check

```bash
$ caliper update --check
```

Or even more specifically, for one library or metric:

```bash
caliper update --metric functiondb pypi:sif
```

And of course if you add a new module or metric, you can simply add it to the
[caliper.yaml](caliper.yaml) here to ensure that updates occur regularly.


## Manual Extraction

If you want to add an entirely new module, you might want to extract the
metrics that you want first! Example manual extractions looks like this:

```bash
$ caliper extract pypi:sif --metric functiondb
```

or for a larger project (that we need zip for)

```bash
$ caliper extract --metric functiondb --fmt zip pypi:tensorflow
```

to generate output in the present working directory under [pypi](pypi) or another
package manager, respectfully. Each metric output file is organized by a complete
version (e.g., `0.0.11`) in the case of a `MetricBase`, or a range (e.g., `0.0.1..0.0.11`)
in the case of a `ChangeMetric`. The data under that depends on the metric. For example,
`changedfiles` might have a lookup for different kinds of changes, while `functiondb` might
be a lookup of functions and arguments organized by module.

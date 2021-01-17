# Caliper Metrics

This is a repository of extracted metrics data using [caliper](https://github.com/vsoch/caliper). 
Both the library and data repository are under development. Example extractions looks like this:

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

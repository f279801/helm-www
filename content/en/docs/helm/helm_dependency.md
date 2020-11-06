---
title: "Helm Dependency"
---

## helm dependency

manage a chart's dependencies

### Synopsis


Manage the dependencies of a chart.

Helm charts store their dependencies in 'charts/'. For chart developers, it is
often easier to manage dependencies in 'Chart.yaml' which declares all
dependencies.

The dependency commands operate on that file, making it easy to synchronize
between the desired dependencies and the actual dependencies stored in the
'charts/' directory.

For example, this Chart.yaml declares two dependencies:

    # Chart.yaml
    dependencies:
    - name: nginx
      version: "1.2.3"
      repository: "https://example.com/charts"
    - name: memcached
      version: "3.2.1"
      repository: "https://another.example.com/charts"


The 'name' should be the name of a chart, where that name must match the name
in that chart's 'Chart.yaml' file.

The 'version' field should contain a semantic version or version range.

The 'repository' URL should point to a Chart Repository. Helm expects that by
appending '/index.yaml' to the URL, it should be able to retrieve the chart
repository's index. Note: 'repository' can be an alias. The alias must start
with 'alias:' or '@'.

Starting from 2.2.0, repository can be defined as the path to the directory of
the dependency charts stored locally. The path should start with a prefix of
"file://". For example,

    # Chart.yaml
    dependencies:
    - name: nginx
      version: "1.2.3"
      repository: "file://../dependency_chart/nginx"

If the dependency chart is retrieved locally, it is not required to have the
repository added to helm by "helm add repo". Version matching is also supported
for this case.


### Options

```
  -h, --help   help for dependency
```

### Options inherited from parent commands

```
      --debug                       enable verbose output
      --kube-apiserver string       the address and the port for the Kubernetes API server
      --kube-as-group stringArray   Group to impersonate for the operation, this flag can be repeated to specify multiple groups.
      --kube-as-user string         Username to impersonate for the operation
      --kube-context string         name of the kubeconfig context to use
      --kube-token string           bearer token used for authentication
      --kubeconfig string           path to the kubeconfig file
  -n, --namespace string            namespace scope for this request
      --registry-config string      path to the registry config file (default "~/.config/helm/registry.json")
      --repository-cache string     path to the file containing cached repository indexes (default "~/.cache/helm/repository")
      --repository-config string    path to the file containing repository names and URLs (default "~/.config/helm/repositories.yaml")
```

### SEE ALSO

* [helm](helm.md)	 - The Helm package manager for Kubernetes.
* [helm dependency build](helm_dependency_build.md)	 - rebuild the charts/ directory based on the Chart.lock file
* [helm dependency list](helm_dependency_list.md)	 - list the dependencies for the given chart
* [helm dependency update](helm_dependency_update.md)	 - update charts/ based on the contents of Chart.yaml

###### Auto generated by spf13/cobra on 29-Oct-2020
# qBittorrent client

This is a helm chart for [qbittorrent](https://qbittorrent.org/) leveraging the [Linuxserver.io image](https://hub.docker.com/r/linuxserver/qbittorrent/)

## TL;DR;

```shell
$ helm repo add k8s-at-home https://k8s-at-home.com/charts/
$ helm install k8s-at-home/qbittorrent
```

## Installing the Chart

To install the chart with the release name `my-release`:

```console
helm install --name my-release k8s-at-home/qbittorrent
```

The default login details (change ASAP) are:

* login:admin
* password:adminadmin

## Uninstalling the Chart

To uninstall/delete the `my-release` deployment:

```console
helm delete my-release --purge
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

## Configuration
Read through the media-common [values.yaml](https://github.com/k8s-at-home/charts/blob/master/charts/media-common/values.yaml)
file. It has several commented out suggested values.

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`. For example,
```console
helm install qbittorrent \
  --set qbittorrent.env.TZ="America/New York" \
    k8s-at-home/qbittorrent
```
Alternatively, a YAML file that specifies the values for the above parameters can be provided while installing the
chart. For example,
```console
helm install qbittorrent k8s-at-home/qbittorrent --values values.yaml 
```

These values will be nested as it is a dependency, for example
```yaml
qbittorrent:
  image:
    tag: ...
```

---
**NOTE**

If you get
```console
Error: rendered manifests contain a resource that already exists. Unable to continue with install: existing resource conflict: ...`
```
it may be because you uninstalled the chart with `skipuninstall` enabled, you need to manually delete the pvc or use `existingClaim`.

---

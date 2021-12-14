Tilt Bug: Unexpected Triggers
=============================

# Repro Steps

```bash
$ git clone https://github.com/rwoll/tilt-trigger-too-much-repro.git
$ cd tilt-trigger-too-much-repro
$ tilt up
```

Once Tilt shows green on all resources, do:

```
$ touch ./deps/example.txt
```

## Expected

`core` resource rebuilds, but `extra` remains off/untriggered.

## Actual

`extra`, despite not yet being manually init'd/triggered, builds and runs.

NB: They both depend on `./deps/example.txt` in their Docker build, but I wouldn't
expect `extra` to come to life based solely on that.

# `tilt doctor`

```
Tilt: v0.23.2, built 2021-12-03
System: darwin-amd64
---
Docker
- Host: [default]
- Server Version: 20.10.8
- API Version: 1.41
- Builder: 2
- Compose Version: v1.29.2 (build 5becea4c)
---
Kubernetes
- Env: docker-for-desktop
- Context: docker-desktop
- Cluster Name: docker-desktop
- Namespace: default
- Container Runtime: docker
- Version: v1.21.5
- Cluster Local Registry: none
---
```

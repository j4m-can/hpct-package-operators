# HPCT Package Operators

This repository provides HPC package related charms:
* [hpct-gpu-nvidia](gpu-nvidia/README.md)
* [hpct-infiniband](infiniband/README.md)
* [hpct-mpich](mpich/README.md)
* [hpct-openmpi](openmpi/README.md)

These are subordinate charms that are meant to be used as part of an
HPC cluster, deployed under node charms (see hpct-node) as part of
a hpct cluster bundle.

## Test

Prerequisites:
* snap
* charmcraft (snap package)
* juju (snap package)

Clone this repository:

```
git clone <repourl>
```

Build (may need to run each `charmcraft` twice):

```
cd hpct-package-operators
(cd infiniband; charmcraft -v pack)
...
```

Symlink:

```
ln infiniband/hpct-infiniband_ubuntu-22.04-amd64.charm .
...
```

Deploy (e.g., to a compute node):

```
juju deploy hpct-infiniband_ubuntu-22.04-amd64.charm
juju relate compute:node hpct-infiniband:node
...
```

Watch:

```
juju status --watch 5s --relations
```

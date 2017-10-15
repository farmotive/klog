The purpose of `klog` is to avoid mouse interaction while retrieving logs from k8s pods.  Traditionally, if one wanted to exec into a kubernetes container, one had to `kubectl get pods --namespace foo`, visually identify the pod of interest, copy that pod to the buffer, and then `kubectl --namespace foo logs <paste_buffer>` to retrieve the pod's logs.  This simple utility aims to provide a namespace-specific pod selector for quick execution.

# klog

#[![asciicast](https://asciinema.org/a/placeholder.png)](https://asciinema.org/a/placeholder)

```sh
klog(1)

NAME
    klog - Quick k8s pod log utility.

REQUIRES
    kubectl(1)

SYNOPSIS
    klog [OPTIONS]

DESCRIPTION
    ${SCRIPT} is a quick kubernetes (k8s) utility to retrieve pod logs. ${SCRIPT} prompts for:
      - <NAMESPACE> (defaults to current ns. See kubens(1))
      - <POD> (defaults to "1")
      - <CONTAINER> (If the pod has only one container, the logs are immediately retrieved.  
        If the pod has multiple containers, you will be prompted to select one.)
    ENTER to use defaults.

OPTIONS
    -h, --help
        Show this help message

SEE ALSO
    kubectx(1), kubens(1)
```

### USAGE

```sh
$ kex
Namespace? (default qux):
    1 qux
    2 quux
    3 quuz
    4 corge
    5 grault
    6 garply
    7 waldo
    8 fred
    9 plugh
    10 xyzzy
    11 thud
4
Pod number? (default 1):
    1 foo-drupal
    2 bar-mariadb
    3 baz-alpine
2
Command? (default bash)
mysql

Welcome to the MariaDB monitor.  Commands end with ; or \g.
MariaDB [NAME]>
```

## Installation

**For macOS:**

Use the [Homebrew](https://brew.sh/) package manager:
```sh
brew tap farmotive/k8s
brew install kex
```
**NOTE:** If using gcloud sdk to manage the installation and versioning of `kubectl`, install with the `--without-kubernetes-cli` flag to omit the brew dependency:
```sh
brew install kex --without-kubernetes-cli
```

See [farmotive homebrew k8s install section](https://github.com/farmotive/homebrew-k8s#install) for more options.

**Other platforms:**

- Download the `kex` script
- Add it somewhere in your PATH
- Make it executable (`chmod +x`)

-----

Disclaimer: This is not an official Google product.

Thanks to [ahmetb](https://github.com/ahmetb) for the inspiration!

# Kubetail

Kubefwd is a command-line utility that allows users to easily bulk forward services from a Kubernetes namespace to their local workstation, making it convenient for local development and debugging by routing traffic directly to their machine without manual port forwarding configuration. This tool simplifies the process of accessing services running in a Kubernetes cluster from a local development environment.

The tool can be installed as follows:
- Linux and macOS: `wget -O $HOME/.local/bin/kubetail https://raw.githubusercontent.com/johanhaleby/kubetail/master/kubetail && chmod +x $HOME/.local/bin/kubetail`

## Usage

First find the names of all your pods:
```shell
$ kubectl get pods
```

This will return a list looking something like this:
```shell
NAME                   READY     STATUS    RESTARTS   AGE
app1-v1-aba8y          1/1       Running   0          1d
app1-v1-gc4st          1/1       Running   0          1d
app1-v1-m8acl  	       1/1       Running   0          6d
app1-v1-s20d0  	       1/1       Running   0          1d
app2-v31-9pbpn         1/1       Running   0          1d
app2-v31-q74wg         1/1       Running   0          1d
my-demo-v5-0fa8o       1/1       Running   0          3h
my-demo-v5-yhren       1/1       Running   0          2h
```

To tail the logs of the two "app2" pods in one go simply do:

```shell
$ kubetail app2
```

To tail only a specific container from multiple pods specify the container like this:

```shell
$ kubetail app2 -c container1
```

You can repeat -c to tail multiple specific containers:
```shell
$ kubetail app2 -c container1 -c container2
```

To tail multiple applications at the same time seperate them by comma:

```shell
$ kubetail app1,app2
```

For advanced matching you can use regular expressions:

```shell
$ kubetail "^app1|.*my-demo.*" --regex
```

To tail logs within a specific namespace, make sure to append the namespace flag after you have provided values for containers and applications:

```shell
$ kubetail app2 -c container1 -n namespace1
```

## More information

https://github.com/johanhaleby/kubetail

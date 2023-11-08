# Kubefwd

Kubefwd is a command-line utility that allows users to easily bulk forward services from a Kubernetes namespace to their local workstation, making it convenient for local development and debugging by routing traffic directly to their machine without manual port forwarding configuration. This tool simplifies the process of accessing services running in a Kubernetes cluster from a local development environment.

The tool can be installed as follows:
- Linux and macOS: `brew install txn2/tap/kubefwd`
- Winows: `scoop install kubefwd`
-> Or via source: [https://github.com/txn2/kubefwd/releases](https://github.com/txn2/kubefwd/releases)

## Usage

Forward all svc for the namespace the-project: `sudo kubefwd svc -n the-project`

Forward all svc for the namespace the-project where labeled system: wx: `sudo kubefwd svc -l system=wx -n the-project`

Forward a single service named my-service in the namespace the-project: `sudo kubefwd svc -n the-project -f metadata.name=my-service`

Forward more than one service using the in clause: `sudo kubefwd svc -l "app in (app1, app2)"`

## More information

-> [https://github.com/txn2/kubefwd](https://github.com/txn2/kubefwd)
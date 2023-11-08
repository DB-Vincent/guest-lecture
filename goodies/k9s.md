# K9s

K9s is a powerful, terminal-based user interface (TUI) that simplifies and enhances the management of Kubernetes clusters, allowing users to efficiently navigate, inspect, and interact with cluster resources. With features like real-time updates and resource filtering, K9s provides a seamless and intuitive way to monitor and control Kubernetes workloads from the command line.

The tool can be installed using "Webi":
- Linux and macOS: `curl -sS https://webinstall.dev/k9s | bash`
- Windows: `curl.exe -A MS https://webinstall.dev/k9s | powershell`

## Usage

K9s uses aliases to navigate most K8s resources.

| Action                                                         | Command                       | Comment                                                                |
|----------------------------------------------------------------|-------------------------------|------------------------------------------------------------------------|
| Show active keyboard mnemonics and help                        | `?`                           |                                                                        |
| Show all available resource alias                              | `ctrl-a`                      |                                                                        |
| To bail out of K9s                                             | `:q`, `ctrl-c`                |                                                                        |
| View a Kubernetes resource using singular/plural or short-name | `:`po⏎                        | accepts singular, plural, short-name or alias ie pod or pods           |
| View a Kubernetes resource in a given namespace                | `:`alias namespace⏎           |                                                                        |
| Filter out a resource view given a filter                      | `/`filter⏎                    | Regex2 supported ie `fred|blee` to filter resources named fred or blee |
| Inverse regex filter                                           | `/`! filter⏎                  | Keep everything that *doesn't* match.                                  |
| Filter resource view by labels                                 | `/`-l label-selector⏎         |                                                                        |
| Fuzzy find a resource given a filter                           | `/`-f filter⏎                 |                                                                        |
| Bails out of view/command/filter mode                          | `<esc>`                       |                                                                        |
| Key mapping to describe, view, edit, view logs,...             | `d`,`v`, `e`, `l`,...         |                                                                        |
| To view and switch to another Kubernetes context (Pod view)    | `:`ctx⏎                       |                                                                        |
| To view and switch directly to another Kubernetes context (Last used view) | `:`ctx context-name⏎          |                                                                        |
| To view and switch to another Kubernetes namespace             | `:`ns⏎                        |                                                                        |
| To view all saved resources                                    | `:`screendump or sd⏎          |                                                                        |
| To delete a resource (TAB and ENTER to confirm)                | `ctrl-d`                      |                                                                        |
| To kill a resource (no confirmation dialog, equivalent to kubectl delete --now)                   | `ctrl-k`                      |                                                                        |
| Launch pulses view                                             | `:`pulses or pu⏎              |                                                                        |
| Launch XRay view                                               | `:`xray RESOURCE [NAMESPACE]⏎ | RESOURCE can be one of po, svc, dp, rs, sts, ds, NAMESPACE is optional |
| Launch Popeye view                                             | `:`popeye or pop⏎             | See [popeye](#popeye)                                               |

## More information

-> [https://github.com/derailed/k9s](https://github.com/derailed/k9s) 
# aks-node-debug

A `kubectl` plugin that simplifies node-level troubleshooting in Kubernetes clusters, with a primary focus on Azure Kubernetes Service (AKS).

The plugin automatically discovers cluster nodes, allows you to select a node interactively, and launches a debug session using `kubectl debug`.

## Features

* Lists available cluster nodes interactively
* Allows node selection from a menu
* Creates a debug pod on the selected node
* Opens a shell directly on the node for troubleshooting
* Simplifies the standard `kubectl debug node/<node-name>` workflow
* Supports any Kubernetes cluster where `kubectl debug` is available

## Prerequisites

* Kubernetes cluster with node debugging enabled
* `kubectl` installed and configured
* Azure CLI installed and authenticated (`az login`)
* Sufficient RBAC permissions to:

  * List nodes
  * Create debug pods
* Kubernetes version that supports `kubectl debug`

## Installation

### Manual Installation

```bash
git clone https://github.com/ragatgen/kubectl-aks-node-debug.git

cd kubectl-aks-node-debug

chmod +x kubectl-aks-node-debug

sudo install -m 755 kubectl-aks-node-debug /usr/local/bin/
```

### Verify Installation

```bash
kubectl plugin list
```

Expected output:

```text
/usr/local/bin/kubectl-aks-node-debug
```

## Usage

Launch the plugin:

```bash
kubectl aks node debug
```

Display help:

```bash
kubectl aks node debug --help
```

Display version:

```bash
kubectl aks node debug --version
```

## Example

```text
Using Kubernetes context: MyAKS

Available cluster nodes:

1) aks-agentpool-16270128-vmss000000
2) aks-userpool-16270128-vmss000000
3) aks-userpool-16270128-vmss000001

Choose one node by number: 2

You selected: aks-userpool-16270128-vmss000000

Starting debug session on node: aks-userpool-16270128-vmss000000

Creating debugging pod node-debugger-aks-userpool-16270128-vmss000000-xxxxx with container debugger on node aks-userpool-16270128-vmss000000.

If you don't see a command prompt, try pressing Enter.

root@aks-userpool-16270128-vmss000000:/#
```

## How It Works

The plugin:

1. Verifies that `kubectl` is installed.
2. Verifies that Azure CLI is installed and authenticated.
3. Retrieves the current Kubernetes context.
4. Validates permissions to list nodes and create pods.
5. Retrieves the list of cluster nodes.
6. Presents an interactive node selection menu.
7. Executes a `kubectl debug` session against the selected node.
8. Opens a shell for node-level investigation and troubleshooting.

## Common Use Cases

* Investigating node health issues
* Troubleshooting networking problems
* Inspecting the host filesystem
* Verifying node configuration
* Collecting diagnostics during incident response
* Analyzing node-level Kubernetes issues

## Version

Display the installed plugin version:

```bash
kubectl aks node debug --version
```

Example output:

```text
kubectl-aks-node-debug 0.1.1
```

## License

MIT License

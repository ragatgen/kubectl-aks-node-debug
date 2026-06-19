# aks-debug-node

This repository provides a `kubectl` plugin to debug nodes in your AKS (Azure Kubernetes Service) cluster.

## Installation

```bash
git clone https://github.com/ragatgen/aks-debug-node.git
cd aks-debug-node
sudo mv aks-debug-node /usr/local/bin/
sudo chmod +x /usr/local/bin/aks-debug-node
```

## Verify Installation

Run the following command to list installed plugins:

```bash
kubectl plugin list
```

Expected output:
```
/usr/local/bin/aks-debug-node
```

## Usage

To start debugging a node in your AKS cluster:

```bash
aks-debug-node
```

Example interaction:

```
Available nodes in your AKS cluster:
1) aks-default-99999999-vmss000000
2) aks-default-99999999-vmss000001
3) aks-default-99999999-vmss000002
Choose one node by number: 2
You selected: aks-default-99999999-vmss000001
Debugging node: aks-default-99999999-vmss000001...
Creating debugging pod node-debugger-aks-default-99999999-vmss000001-njktc with container debugger on node aks-default-99999999-vmss000001.
If you don't see a command prompt, try pressing enter.
root@aks-default-99999999-vmss000001:/#
```

![](./docs/kubeUPS_logo.png)
####
`kubeUPS` is a easy-to-install helm chart that allows you to monitor UPS (battery-backup) devices plugged-into your kubernetes clusters. 

![](./docs/screenshot.png)

## What's this for? 💻
This collection of Docker images deploys a full monitoring stack needed to get you counting those watts with a fine-tooth comb. 

### Containers
 * [apcupsd](https://github.com/bgulla?tab=repositories&q=apcupsd)
 * [apcupsd_exporter](https://github.com/mdlayher/apcupsd_exporter) by [mdlayher](https://github.com/mdlayher)
 * grafana
 * prometheus

## Prerequesites
 * a Kubernetes cluster. I personally recommend [k3s](https://k3s.io) with USB-based UPS devices plugged in to random kubelets.
 * nodes labeled with `has_ups=true`
 * a valid [helm](https://helm.sh) installation
 * at least 1 `amd64`-architectured kubelet (for now)

## Installation (tldr)
```bash
    # label nodes with UPS Devices
    kubectl label node node1 has_ups=true

    # install helm chart   
    git clone https://github.com/bgulla/kubeups.git
    cd kubeups
    helm upgrade --install kubeups chart/kubeups --debug
    echo "profit!"
```

## TODO
* Make sure that this works with a pure ARMv7 environment (easy)
* Fully template out the `values.yml` file (easy)
* deploy a smtp-forwarder for email alerts (moderate time dedication)
* auto-create ingress (easy)


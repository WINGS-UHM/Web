---
layout: page
menubar: oran_menu
title: Installation
subtitle: Getting Started
show_sidebar: false
toc: true
---

## Overview
```sh
git clone https://github.com/WINGS-UHM/O-RAN.git
cd O-RAN/NearRT-RIC
```
The following scripts are prepared for installing `kubespray` and `docker` based kubernetes cluster for deploying the Near RT-RIC
```yaml
NEAR-RT-RIC/
├── nginx.sh                            # setup nginx service for hosting dashboards (grafana, kubernetes)
├── kubespray.sh                        # setup a single node kubspray cluster with calico and metallb
├── kube-extra.sh                       # extra setups for setting up dashboard and nfs volumes for influxdb
├── fix-dns.sh                          # fixes dns/internet disconnection if setup breaks nameserver 
├── get-env.sh                          # helper funtion to export import ric-plt ips
└── install_common_templates_to_helm.sh # Modified common templates script to remove root access dependency
```
## Kubernetes Cluster Deployment
```sh
sudo chmod +x *.sh
./nginx.sh
./kubespray.sh
./kube-extra.sh
```
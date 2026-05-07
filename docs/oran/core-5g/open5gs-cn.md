---
layout: page
title: Core Network Setup
# subtitle: Pages
menubar: oran_menu
toc: true
show_sidebar: false
---

## OCUDU Installation

Install `ZMQ` for simulations
```sh
# 
sudo apt-get install libzmq3-dev
```

Install the `OCUDU` using the following commands
```sh
# Install OCUDU with ZMQ-enabled
git clone https://gitlab.com/ocudu/ocudu.git
cd ocudu
mkdir build
cd build
cmake ../ -DENABLE_EXPORT=ON -DENABLE_ZEROMQ=ON 
make -j`nproc`
```

## Deploying Core Network

We deploy the core network using the Docker images provided in the `ocudu` library from `open5gs`

```sh
docker compose -f docker-compose.yml up --build 5gc
```

Additionally you can also launch the grafana dashboard for metrics monitoring using 

```sh
docker compose -f docker-compose.yml -f docker-compose.ui.yml up --build 5gc
```
the dashboard will be hosted at `localhost:3300` and the WebUI with subscriber database will be at `localhost:9999` you can add new subscribers before launching in the `open5gs/subscriber_db.csv` or from the WebUI. 



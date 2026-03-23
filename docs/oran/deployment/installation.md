---
layout: page
title: Near RT-RIC deployment
menubar: oran_menu
toc: true
show_sidebar: false
---

## Near RT-RIC deployment
```sh
git clone https://gerrit.o-ran-sc.org/r/ric-plt/ric-dep
cp ./install_common_templates_to_helm.sh ./ric-dep/bin
cd ric-dep/bin
./install_common_templates_to_helm.sh
version=j   # change variable according to release preference.
./install -f ../RECIPE_EXAMPLE/example_recipe_oran_${version}_release.yaml -c "influxdb jaegeradapter"
```
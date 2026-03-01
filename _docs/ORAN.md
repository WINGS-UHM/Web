---
title: "ORAN Testbed"
subtitle: 
# description: This is a course description
layout: docs-2
image: /assets/img/project/Testbed.svg
# semester: 2024-2025
menubar: oran_menu
features:
    - label: Holmes Hall 488, UHM, Honolulu, HI
      icon: fa-location-arrow
    - label: 2026 Spring
      icon: fa-calendar
---

# Infrastructure 
The entire O-RAN testbed is deployed on two high-performance Ubuntu-based infrastructure, providing a stable and scalable foundation for Kubernetes, O-RAN services, and RAN experimentation.

- **Host OS:** Ubuntu 24.04.3 LTS (x86_64)
- **CPU:** AMD Ryzen 9 9950X3D (32 threads, high clock performance)
- **Memory:** 64 GB RAM
- **GPU:** NVIDIA RTX 5070ti
- **USRPs:** 1x x410, 1x x310
- **Software:**  [OCUDU](https://github.com/WINGS-UHM/ocudu), [srsGUI](https://github.com/WINGS-UHM/srsGUI), [srsRAN_4G](https://github.com/WINGS-UHM/srsRAN_4G)

We have prepared forks of the upstream repositories with enhanced metric plotting, extended telemetry exposure, and customized capabilities tailored to support advanced O-RAN experimentation and real-time performance analysis within the testbed.
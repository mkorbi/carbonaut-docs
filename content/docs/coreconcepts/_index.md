---
Title: Core Concepts
weight: 10
---

## How Carbonaut works

Carbonaut utilizes the cloud API of AWS to receive utilization data of the cloud resources. It integrates against an API that delivers power and CO2 data. For the Carbon Hack of the GSF, the first API is the Wattime API. 

Prometheus, on the other hand, delivers metrics from Kubernetes clusters. This could be done through OpenTelemetry or the Grafana Agent too. However, Prometheus is typically present in most clusters.

Carbonaut combines the utilization data with watt and CO2 data and the avrg. power consumption of the hardware.
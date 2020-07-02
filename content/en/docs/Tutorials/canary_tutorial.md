---
title: "Canary Tutorial"
date: 2020-05-14
weight: 5
description: >
  Simple Web App With a Monitoring System.
---

* Optimize a simple web app that already has monitoring
* Artifacts at: co-http/k8s-prom
  web.yaml - deployment using co-http and service
  opsani-servo.yaml - configmap + servo deployment resources
  rbac.yaml - service account setup for servo to access k8s api (link?)
  prometheus.yaml - Prometheus setup (link?)
* Servo: Kubernetes + Prometheus + Vegeta + magg
* single co-http deployment, named "app"
* vegeta load profile and with NO metrics
* Prometheus metrics configured for co-http
* By default, optimizes for best efficiency (throughput vs. cost) [co-http currently does not provide response time metrics, so no time-SLO optimization possible]
* settings: cpu and replicas (consider memory as well, to see it minimize it)
* README may include a short YAML user configuration (fka config-state.yaml) that contains primarily the optimization goal and load control vars
* README instructs how to:
  * deploy app
  * do first optimization
  * change optimization goal (e.g., change spp as "prefer better perf" vs. "prefer cost savings") and reoptimize
  * change workload (i.e., change busy parameter) emulating new app versions and reoptimize



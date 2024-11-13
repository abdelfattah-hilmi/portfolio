---
title: "fluentd config to push logs to loki"
excerpt: "fluentd config to push logs to loki"
publishDate: "2024-11-04T16:58:36.050Z"
image: "https://devio2023-media.developers.io/wp-content/uploads/2019/05/fluentd_1200_630.png"
category: "Docs"
author: "Abdelfattah Hilmi"
layout: "@layouts/BlogLayout.astro"
tags: [Cloud, Devsecops, SRE]
---









## fluentd config to push logs to loki

Fluentd will run on every node in the cluster to collect logs from Kubernetes pods and forward them to Loki.

Create a ConfigMap for Fluentd:

Define the Fluentd configuration to send logs to Loki.

```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: fluentd-config
  namespace: monitoring
data:
  fluent.conf: |
    <source>
      @type tail
      path /var/log/containers/*.log
      pos_file /var/log/fluentd-containers.log.pos
      tag kubernetes.*
      format json
      time_format %Y-%m-%dT%H:%M:%S.%NZ
      read_from_head true
    </source>

    <filter kubernetes.**>
      @type kubernetes_metadata
    </filter>

    <match **>
      @type loki
      url "http://loki:3100/loki/api/v1/push"  # Update URL to point to your Loki service
      <label>
        job
        instance
        namespace
        pod_name
        container_name
      </label>
      <buffer>
        @type file
        path /var/log/fluentd-buffers
        flush_interval 10s
        chunk_limit_size 2M
        queue_limit_length 256
        retry_forever true
        retry_max_interval 30
      </buffer>
    </match>
```

Apply the ConfigMap:

```bash
kubectl apply -f fluentd-config.yaml
```
Create the Fluentd DaemonSet:

Define a DaemonSet to run Fluentd on every node in the Kubernetes cluster.

```yaml
apiVersion: apps/v1
kind: DaemonSet
metadata:
  name: fluentd
  namespace: monitoring
spec:
  selector:
    matchLabels:
      name: fluentd
  template:
    metadata:
      labels:
        name: fluentd
    spec:
      serviceAccountName: fluentd
      containers:
        - name: fluentd
          image: fluent/fluentd-kubernetes-daemonset:v1.13.3-debian-loki
          env:
            - name: FLUENT_ELASTICSEARCH_HOST
              value: "loki:3100"
            - name: FLUENT_ELASTICSEARCH_PORT
              value: "3100"
          volumeMounts:
            - name: varlog
              mountPath: /var/log
            - name: config
              mountPath: /fluentd/etc/fluent.conf
              subPath: fluent.conf
      volumes:
        - name: varlog
          hostPath:
            path: /var/log
        - name: config
          configMap:
            name: fluentd-config
```
Apply the DaemonSet:

```bash
kubectl apply -f fluentd-daemonset.yaml
```
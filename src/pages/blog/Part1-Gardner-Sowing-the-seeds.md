---
title: "K8S at scale - Gardener step 1: sowing the seeds  "
excerpt: "K8S at scale - Gardener step 1: sowing the seeds  "
publishDate: "2025-09-15T23:07:07.071Z"
image: "https://demo.gardener.cloud/static/cluster-hierarchy.png"
category: "Docs"
author: "Abdelfattah Hilmi"
layout: "@layouts/BlogLayout.astro"
tags: [Cloud, Devsecops, SRE]
---

## Getting Started with Gardener 🌱

Soooo, picture this: Kubernetes clusters are like little gardens, and Gardener? Well… it's the ultimate garden manager. It waters your clusters, trims the weeds, and makes sure nothing dies while you’re binge-watching a series. Now, normally, I’m picky about the tools I add to my HomeLab—I like to stick to a stack until I know it like the back of my hand. But… dammit, Gardener is so cool you just can’t ignore it—even if I technically have no use for it. LOL.

Let’s dive in.


![high level architecture](https://demo.gardener.cloud/static/cluster-hierarchy.png)
---

### Focus on the Most Important: What is a Shoot?

In Gardener lingo, a **Shoot** is a Kubernetes cluster managed by Gardener. Think of it as your “garden bed”: you specify what you want planted, how big it should be, and what type of soil (infrastructure) it needs. Gardener then makes sure it grows exactly how you envisioned.

The `Shoot` resource includes things like:

- Kubernetes version 🌟
- Infrastructure type 🏗️
- Machine types 🖥️


---

### Planting Your First Shoot 🌿

Let’s get our hands dirty and create a Shoot. First, you need a YAML file describing your desired cluster state. Then in your terminal:

`kubectl apply -f example/provider-local/shoot.yaml`

This tells Gardener: _“Hey, make this cluster happen!”_

While the cluster grows (this usually takes a few minutes), let’s peek inside the Shoot resource. Use:

`kubectl explain shoot kubectl explain shoot.spec`

This will show you what all the fields mean. Nerdy? Yes. Useful? Totally.

To watch the creation process:

`kubectl get shoot local --watch`

Sit back and watch your cluster bloom. Congratulations! 🎉 You’ve just planted your first Shoot.

---

### Interacting with Your Shoot 🌻

Once your Shoot is alive, you’ll need a **kubeconfig** to talk to it. In Gardener, you can request either an admin or viewer kubeconfig. For admin access:

`gardenctl target shoot local --garden local eval $(gardenctl kubectl-env bash)`

Now you’re talking to your Shoot cluster. Try listing nodes:

`kubectl get nodes`

Or check out the `kube-system` pods:

`kubectl get pods -n kube-system`

💡 **Tip:** You’re now dealing with two clusters:

1. **Garden cluster** – where you manage Shoot resources.
    
2. **Shoot cluster** – where your apps actually run.
    

Switch back to the Garden cluster anytime with:

`unset KUBECONFIG kubectl get shoot`

---

### Where is the Control Plane? 🏗️

In Gardener, the control plane of a Shoot lives in a **Seed cluster**, another Kubernetes cluster. Normally invisible to users, it runs all the boring-but-critical stuff like ETCD, API servers, controllers, and schedulers.

Check out the Seeds you have:

`kubectl get seed`

The magic happens thanks to the **gardenlet**, which manages your Shoot’s control plane in a way similar to how kubelets manage pods. Each Shoot’s control plane is isolated in its own namespace on the Seed, but shares the underlying nodes—efficient and tidy.

Want to peek inside the control plane? Select the Seed kubeconfig:

`ktx runtime kubectl get pods -n shoot--local--local kubectl get deployments,statefulsets -n shoot--local--local`

You’ll see the usual suspects: ETCD, API server, controller manager, scheduler, plus machine-controller-manager, cluster-autoscaler, and observability goodies.

---

And just like that, you’ve sown the seeds, watched them grow, and peeked behind the curtain at the garden staff doing all the heavy lifting. 🌱
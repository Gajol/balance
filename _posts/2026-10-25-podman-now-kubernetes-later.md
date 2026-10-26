---
layout: single
title: "Podman Now, Kubernetes Later"
date: 2026-10-25 00:20:00 -0400
description: "Write the deployment as Kubernetes YAML from day one. Run it on Podman today and move to a cluster later without a rewrite."
excerpt: "Write the deployment as Kubernetes YAML from day one. Run it on Podman today and move to a cluster later without a rewrite."
theme: digital
author_profile: false
classes: full-width
tags: [devops, architecture]
---
{% include series-nav.html %}

Many teams are not ready for a Kubernetes cluster on day one. The risk is building something that has to be thrown away when they are.

## The idea

Write the deployment as **Kubernetes YAML** from the start. Run it on a single host with **Podman**, using systemd units (Quadlet). When a cluster is ready, apply the same YAML. Only the overlay changes.

## Five rules that keep the move small

1. Author the deployment as Kubernetes YAML, even on Podman.
2. Run the search engine in cluster mode from day one, even with one node.
3. Use Kustomize overlays. No chart repository is needed on an isolated network.
4. Put scheduled jobs in their own units from the start.
5. Set a review date for Podman as a production platform.

## What changes, and what does not

Images, config files and the pipeline promotion rule carry over. Storage, ingress, network policy and the search deployment change. Storage and backup are the biggest items.

## Isolated networks

Build once outside, sign the package, carry it across and promote the same image through every environment. Turn off update checks and downloads. Nothing is fetched at deploy time.

## Go deeper

The [full working paper]({{ '/podman-to-kubernetes/' | relative_url }}) has the work breakdown, code examples, diagrams, a file-by-file change map and sizing.

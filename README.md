# Kavita Helm Chart

Baseline Helm chart for [Kavita](https://www.kavitareader.com) (ebook and comic server). Uses the [bjw-s app-template](https://github.com/bjw-s/helm-charts).

## Subcharts

| Subchart | Source | Values prefix | Description |
|----------|--------|---------------|-------------|
| **kavita** (app-template) | [bjw-s helm-charts](https://github.com/bjw-s/helm-charts) | `kavita.*` | Deployment, library mounts, ingress on port 5000. |

## Key values

| Area | Where | What to set |
|------|--------|-------------|
| Ingress | `kavita.ingress.main.hosts` | Your domain and TLS secret. |
| Libraries | `kavita.persistence.books/comics` | PVC size, storageClass, or `existingClaim`. |
| Config | `kavita.persistence.config` | PVC or `existingClaim` for `/kavita/config`. |
| Resources | `kavita.controllers.main.containers.main.resources` | Scale for large libraries. |

## Install

```bash
helm dependency update .
helm install kavita . -f my-values.yaml -n kavita --create-namespace
```

**From Helm repo (expectedbehaviors):**

```bash
helm repo add kavita https://expectedbehaviors.github.io/kavita
helm install kavita kavita/kavita -f my-values.yaml -n kavita --create-namespace
```

## Render & validation

```bash
helm dependency update . && helm template kavita . -f values.yaml -n kavita
```

## Support this project

I build tools to get the best homelab experience I can from what's available and to grow as a programmer along the way. If you'd like to contribute, donations go toward homelab operating costs and subscriptions that keep this tooling maintained. Optional and appreciated.

[![Donate with PayPal](https://www.paypalobjects.com/en_US/i/btn/btn_donate_LG.gif)](https://www.paypal.com/donate/?business=9RHVW92WMWQNL&no_recurring=0&item_name=Optional+donations+help+support+Expected+Behaviors%E2%80%99+open+source+work.+Thank+you.&currency_code=USD)

# ShopHub Helm Charts

All Helm charts authored by the ShopHub team live in this repository. The structure follows the layout required by the project specification (section 5.3, IaC organization).

## Repository layout

```
helm-charts
├── README.md
└── charts/
    ├── shop/
    │   ├── Chart.yaml
    │   ├── values.yaml
    │   └── templates/
    ├── shop-operator/
    │   ├── Chart.yaml
    │   ├── values.yaml
    │   └── templates/
    └── shophub/
        ├── Chart.yaml
        ├── values.yaml
        ├── charts/
        └── templates/
            ├── NOTES.txt
            ├── _helpers.tpl
            ├── deployment.yaml
            ├── hpa.yaml
            ├── ingress.yaml
            ├── service.yaml
            └── serviceaccount.yaml
```

## Charts

| Chart | What it deploys |
|---|---|
| `charts/shop` | A single-tenant Shop application, used by the shop-operator when a `Shop` custom resource is reconciled. |
| `charts/shop-operator` | The Shop operator Deployment, the CRDs, and the required RBAC. |
| `charts/shophub` | The ShopHub platform web application. Uses `kube-prometheus-stack` as a subchart for the observability stack. |

## Publishing

Charts are packaged and published as OCI artifacts to the GitHub Container Registry under `oci://ghcr.io/shophub-devops/charts`. Versioning follows [Semantic Versioning](https://semver.org/).

## Related repositories

| Repository | Purpose |
|---|---|
| [shophub](https://github.com/ShopHub-DevOps/shophub) | Application deployed by `charts/shophub` |
| [shop](https://github.com/ShopHub-DevOps/shop) | Application deployed by `charts/shop` |
| [shop-operator](https://github.com/ShopHub-DevOps/shop-operator) | Operator deployed by `charts/shop-operator` |
| [kube-state](https://github.com/ShopHub-DevOps/kube-state) | Declarative cluster state that references these charts by OCI URL |

## License

MIT. See [LICENSE](./LICENSE).

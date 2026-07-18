# Shophub Helm Chart

This chart deploys the core Shophub platform including the frontend, backend, PostgreSQL database, and the observability stack (Kube-Prometheus-Stack/Grafana).

## Grafana Authentication

By default, Grafana is completely locked down and anonymous access is disabled. Maintainers can access the Grafana dashboards using a secure administrator account.

**Default Login:**
- Username: `admin`
- Password: `admin` (or the default set in your `values.yaml`)

**Security Best Practice:**
The default password is intentionally committed as a placeholder for local development. **DO NOT** use the default password in production. When installing or upgrading the Helm chart, always inject a strong password and your GitHub OAuth keys via the command line:

```bash
helm upgrade --install shophub ./charts/shophub \
  --namespace default \
  --set grafanaAdminPassword="your-secure-password" \
  --set githubOAuth.clientId="your-github-client-id" \
  --set githubOAuth.clientSecret="your-github-client-secret"
```

This will automatically create a secure Kubernetes Secret containing your password and OAuth keys and mount them into the Grafana container securely.

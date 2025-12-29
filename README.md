# Apache Fineract Helm Chart

## Quick Start

### Configure external database in values.yaml:

```yaml
database:
  host: "postgres.example.com"
  port: 5432
  username: "fineract"
  password: "securepassword"
```

### Install:

```bash
helm install fineract ./fineract-chart
```

## Requirements

- PostgreSQL: External instance reachable from the cluster.
- Privileges: The database user must have CREATEDB permissions for the initial setup.

## Key Configuration

| Value           | Description       | Default       |
| --------------- | ----------------- | ------------- |
| `database.host` | Database hostname | `""`          |
| `image.tag`     | Fineract version  | `1.11.0`      |
| `resources`     | CPU/Memory limits | `1Gi / 1000m` |

## Troubleshooting

### Wait for Init Job:

The init-dbs job runs before the server. If the server doesn't start, check the job:

```bash
kubectl get jobs
kubectl logs -l app.kubernetes.io/instance=fineract
```

### Application Logs:

```bash
kubectl logs -l app=fineract-server -f
```

## Uninstall

```bash
helm uninstall fineract
```

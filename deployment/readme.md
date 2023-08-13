## Coworking Space Service Extension

### Deployment database
- **Deploy postgresql through helm**
```sh
helm repo add bitnami https://charts.bitnami.com/bitnami
helm install postgresql bitnami/postgresql --set primary.persistence.enabled=false --set postgresqlPassword=postgres

```

- **Initiate database**

```sh
# goto db folder
cd db

kubectl port-forward --namespace default svc/postgresql 5432:5432
PGPASSWORD="$POSTGRES_PASSWORD" psql --host 127.0.0.1 -U postgres -d postgres -p 5432 < 1_create_tables.sql
PGPASSWORD="$POSTGRES_PASSWORD" psql --host 127.0.0.1 -U postgres -d postgres -p 5432 < 2_seed_users.sql
PGPASSWORD="$POSTGRES_PASSWORD" psql --host 127.0.0.1 -U postgres -d postgres -p 5432 < 3_seed_tokens.sql
```

## Deployment Application
```sh
cd deployment
```

# PgBouncer

![Version: 0.1.0](https://img.shields.io/badge/Version-0.1.0-informational?style=flat-square)
![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square)
![AppVersion: 1.21.0](https://img.shields.io/badge/AppVersion-1.21.0-informational?style=flat-square)

A Helm chart for deploying bitnami/pgbouncer with TLS encryption and existing secrets.

**Homepage:** <https://github.com/onaio/helm-chart-pgbouncer>

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| Ona | <techops@ona.io> | <https://github.com/onaio> |


## Source Code

* <https://github.com/onaio/helm-chart-pgbouncer>
* <https://bitnami.com/stack/pgbouncer>

## TL;DR

[pgbouncer](https://www.pgbouncer.org/) is a lightweight connection pooler for PostgreSQL.

```console
helm repo add onaio https://onaio.github.io/helm-charts
helm install pgbouncer onaio/pgbouncer
```

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| autoscaling.enabled | bool | `false` | enable autoscaling |
| autoscaling.maxReplicas | int | `100` | max replicas |
| autoscaling.minReplicas | int | `1` |  |
| autoscaling.targetCPUUtilizationPercentage | int | `80` |  |
| autoscaling.targetMemoryUtilizationPercentage | int | `80` |  |
| extraConfigs | list | `[]` | A list of `key: value` pairs to be added to the container's environment. For example, to set the `POSTGRESQL_PASSWORD` environment variable, you can add `POSTGRESQL_PASSWORD: mysecretpassword` to the list. Full list of available environment variables can be found on the [bitnami/pgbouncer](https://github.com/bitnami/containers/tree/main/bitnami/pgbouncer#configuration) image page. |
| extraSecretConfigs | list | `[]` | Same as `extraConfigs` but the values are read from a secret. For example, to set the `POSTGRESQL_PASSWORD` environment variable, you can add `POSTGRESQL_PASSWORD: mysecretpassword` to the list. This will create a secret with the name specified in `extraconfigsSecretName` with the key `POSTGRESQL_PASSWORD` and the value `mysecretpassword`. Note that if createExtraConfigsSecret is set to false, these values will be ignored. |
| createExtraConfigsSecret | bool | `false` | Whether to create a secret with extra configs. If set to true, the secret will be created with the name specified in `extraconfigsSecretName`. If set to false, a secret with the name specified in `extraconfigsSecretName` must exist in the same namespace as the chart is deployed in. |
| extraconfigsSecretName | string | `"pgbouncer-extra-configs"` | Name of the secret to create or use if `createExtraConfigsSecret` is set to false. |
| fullnameOverride | string | `""` |  |
| image.pullPolicy | string | `"IfNotPresent"` |  |
| image.repository | string | `"bitnami/pgbouncer"` |  |
| image.tag | string | `"1.19.1-debian-11-r44"` |  |
| imagePullSecrets | list | `[]` |  |
| ingress.annotations | object | `{}` |  |
| ingress.className | string | `"nginx"` |  |
| ingress.enabled | bool | `false` |  |
| ingress.hosts[0].host | string | `"chart-example.local"` |  |
| ingress.hosts[0].paths[0].path | string | `"/"` |  |
| ingress.hosts[0].paths[0].pathType | string | `"ImplementationSpecific"` |  |
| ingress.tls | list | `[]` |  |
| nameOverride | string | `""` |  |
| pgbouncer.connectQuery | string | `""` |  Query which will be executed after a connection is established. |
| pgbouncer.database | string | `"${PGBOUNCER_DATABASE}"` |  Backend PostgreSQL Database name to connect to. |
| pgbouncer.host | string | `"postgresql"` | Backend PostgreSQL hostname. Default: postgresql |
| pgbouncer.password | string | `""` | Backend PostgreSQL password. The password can be specified using the `POSTGRESQL_PASSWORD` environment variable, which can be set by adding it in an existing secret and setting value of `createExtraConfigsSecret: false` or by adding it in `extraSecretConfigs` if `createExtraConfigsSecret: true` |
| pgbouncer.port | int | `5432` | Backend PostgreSQL port. Default: 5432. |
| pgbouncer.postgresqlDatabase | string | `"${PGBOUNCER_DATABASE}"` |  Backend PostgreSQL Database name to connect to. |
| pgbouncer.setDatabasePassword | string | `"no"` |  |
| pgbouncer.setDatabaseUser | string | `"no"` |  |
| pgbouncer.username | string | `"postgres"` |  |
| podAnnotations | object | `{}` |  |
| podSecurityContext | object | `{}` |  |
| replicaCount | int | `1` |  |
| resources.limits.cpu | string | `"100m"` |  |
| resources.limits.memory | string | `"128Mi"` |  |
| resources.requests.cpu | string | `"100m"` |  |
| resources.requests.memory | string | `"128Mi"` |  |
| service.port | int | `6432` |  |
| service.type | string | `"ClusterIP"` |  |
| serviceAccount.annotations | object | `{}` |  |
| serviceAccount.create | bool | `true` |  |
| serviceAccount.name | string | `""` |  |
| tls.certFilename | string | `"tls.crt"` |  |
| tls.certKeyFilename | string | `"tls.key"` |  |
| tls.certificatesSecret | string | `"oaf-tls"` |  |
| tls.enabled | bool | `true` |  |

## Credits

New revision of the chart took inspiration from [oaf-public-charts/pgbouncer](https://github.com/one-acre-fund/oaf-public-charts/blob/main/charts/pgbouncer/)
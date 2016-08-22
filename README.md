# shinken-pack-collectd-grafana

## Description

This Shinken monitoring pack is used to manage grafana services with our
standard deployment of Collectd.

We request Collectd data using unixsock plugin and collectd-nagios script from
collecd-utils package.

This pack depends to shinken-pack-collectd-base to work

## Objects

### Templates

#### Host templates

* collectd-grafana: Manage all default thresholds and values for services

### Services

| Service name              | Description             | Value specification                            | DS        | Consolidation | Warning variable | Critical variable | Duplicate_foreach variable |
|---------------------------|-------------------------|------------------------------------------------|-----------|---------------|------------------|-------------------|----------------------------|
| Grafana - $KEY$ processes | Check Grafana processes | processes-$VALUE1$/ps_count                    | processes | none          | $VALUE2$         | $VALUE3$          | _grafana_processes         |
| Grafana - $KEY$           | Check listening ports   | tcpconns-$VALUE1$-local/tcp_connections-LISTEN | value     | none          | $VALUE2$         | $VALUE3$          | _grafana_listen            |

## Default values

    _grafana_processes    grafana-server $(grafanaserver)$$(1:)$$(1:)$
    _grafana_listen       Listen 3000 $(3000)$$(1:1)$$(1:1)$

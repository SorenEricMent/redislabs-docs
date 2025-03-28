---
Title: rladmin cluster config
linkTitle: config
description: Updates the cluster's configuration.
weight: $weight
alwaysopen: false
toc: "true"
headerRange: "[1-2]"
tags: ["configured"]
categories: ["RS"]
aliases: 
---

Updates the cluster configuration.

```sh
 rladmin cluster config 
        [ cipher_suites <BoringSSL cipher list> ]
        [ cm_port <number> ]
        [ cm_session_timeout <minutes> ]
        [ cnm_http_port <number> ]
        [ cnm_https_port <number>]
        [ data_cipher_list <openSSL cipher list> ]
        [ debuginfo_path <filepath> ]
        [ handle_redirects { enabled | disabled } ]
        [ http_support { enabled | disabled } ]
        [ ipv6 { enabled | disabled } ]
        [ min_control_TLS_version <control_tls_version>]
        [ min_data_TLS_version <data_tls_version> ]
        [ min_sentinel_TLS_version <sentinel_tls_version> ]
        [ s3_url <URL> ]
        [ saslauthd_ldap_conf </tmp/ldap.conf> ]
        [ sentinel_ssl_policy { allowed | required | disabled} ]
        [ sentinel_cipher_suites <golang cipher list>]
        [ services { cm_server | crdb_coordinator | crdb_worker | mdns_server | pdns_server | saslauthd | stats_archiver } { enabled | disabled } ]
        [ upgrade_mode { enabled | disabled } ]
```

### Parameters

| Parameter | Type/Value | Description |
|-----------|------------|-------------|
| cipher_suites | list of ciphers | Cipher suites used for TLS connections to the admin console (specified in the format understood by the BoringSSL library) |
| cm_port | integer | UI server listening port |
| cm_session_timeout | integer | Timeout in minutes for the CM session
| cmn_http_port | integer | HTTP REST API server listening port |
| cnm_https_port | integer | HTTPS REST API server listening port |
| data_cipher_list | list of ciphers | Cipher suites used by the the data plane (specified in the format understood by the OpenSSL library) |
| debuginfo_path | filepath | Local directory to place generated support package files |
| handle_redirects | 'enabled'<br />'disabled' | Enable or turn off handling DNS redirects when DNS is not configured and running behind a load balancer |
| http_support | 'enabled'<br />'disabled' | Enable or turn off using HTTP for REST API connections |
| ipv6 | 'enabled'<br />'disabled' | Enable or turn off IPv6 connections to the admin console |
| min_control_TLS_version | TLS protocol version | The minimum TLS protocol version that is supported for the control path |
| min_data_TLS_version | TLS protocol version | The minimum TLS protocol version that is supported for the data path |
| min_sentinel_TLS_version | TLS protocol version | The minimum TLS protocol version that is supported for the discovery service |
| s3_url | string | The URL of S3 export and import |
| saslauthd_ldap_conf | filepath | Updates LDAP authentication configuration for the cluster (see [cluster-based LDAP authentication]({{<relref "/rs/security/access-control/ldap/cluster-based-ldap-authentication">}}) or [Kubernetes LDAP configuration]({{<relref "/kubernetes/security/ldap-on-k8s">}})) |
| sentinel_cipher_suites | list of ciphers | Cipher suites used by the discovery service (supported ciphers are implemented by the [golang.org cipher suites package](https://golang.org/src/crypto/tls/cipher_suites.go)) |
| sentinel_ssl_policy | 'allowed'<br />'required'<br />'disabled' | Define the SSL policy for the discovery service |
| services | 'cm_server'<br />'crdb_coordinator'<br />'crdb_worker'<br />'mdns_server'<br />'pdns_server'<br />'saslauthd'<br />'stats_archiver'<br /><br />'enabled'<br />'disabled' | Enable or deactivate selected cluster services |
| upgrade_mode | 'enabled'<br />'disabled' | Enable or deactivate upgrade mode on the cluster |

### Returns

Reports whether the cluster was configured successfully. Displays an error message if the configuration attempt fails.

### Example

```sh
$ rladmin cluster config cm_session_timeout_minutes 20
Cluster configured successfully
```

# Entro

## Overview

[Entro Security](https://entro.security/) allows you to discover, monitors, and protects non-human identities (NHIs) and secrets. Entro Security also provides management of the lifecycle of these identities and secrets, from creation to rotation.

Use the Entro integration to monitor your exposed secrets and types. Then visualize that data in Kibana, create alerts to notify you if something goes wrong, and reference audit logs when troubleshooting an issue.

For example, if you wanted to see what types of secrets are being exposed more than usual you could look at the audit logs to isolate this information.

## Data streams
The Entro Security integration collects logs that help you keep a record of security events related to Non-Human Identities (NHIs) and secrets. Right

**Audit:** Audit allows collecting Audit Log Events
The Audit data stream collects detailed events about exposed secrets discovered by the Entro platform. This includes the type of secret, where it was found, and the value of the secret itself. See more details in the Logs reference.

## Requirements
You need Elasticsearch for storing and searching your data and Kibana for visualizing and managing it. You can use our hosted Elasticsearch Service on Elastic Cloud, which is recommended, or self-manage the Elastic Stack on your own hardware.

This integration has the following third-party requirements:

An active Entro Security platform subscription.
An API Token generated from the Entro Security platform with permissions to access the audit log endpoints.


## Setup

### Before setting up the integration, you will need credentials to connect to the Entro Security API.

Log in to your Entro Security platform and generate an API Token. Note this token securely.
Identify the base URL for your Entro API endpoint.

When prompted during setup, you will need to provide the following information:


## Reference

## Logs reference

### Audit

The audit data stream provides events from the Entro Security /v1/scan/auditLogs endpoint. This data stream enriches the raw logs with ECS fields and categorizes the event for security analysis.

#### Example

**Exported fields**

An example event for `audit` looks as following:

```json
{
    "@timestamp": "2025-05-27T20:12:44.000Z",
    "agent": {
        "ephemeral_id": "2edd925c-7d35-4c62-9ee3-de3e924a9a16",
        "id": "430bf95a-cf71-4fb6-be61-9eb7470628f4",
        "name": "elastic-agent-46061",
        "type": "filebeat",
        "version": "8.17.4"
    },
    "data_stream": {
        "dataset": "entro.audit",
        "namespace": "41903",
        "type": "logs"
    },
    "ecs": {
        "version": "8.11.0"
    },
    "elastic_agent": {
        "id": "430bf95a-cf71-4fb6-be61-9eb7470628f4",
        "snapshot": false,
        "version": "8.17.4"
    },
    "event": {
        "agent_id_status": "verified",
        "category": [
            "vulnerability"
        ],
        "created": "2025-05-27T20:12:44.000Z",
        "dataset": "entro.audit",
        "hash": "P+ftR9PJeiuytETRTqMeXXqfSH4=",
        "id": "105d6a3d-6468-4fcc-994e-f525011c53cf",
        "ingested": "2025-07-03T20:46:12Z",
        "kind": "event",
        "type": [
            "info"
        ]
    },
    "host": {
        "architecture": "aarch64",
        "containerized": false,
        "hostname": "elastic-agent-46061",
        "ip": [
            "172.19.0.2",
            "172.18.0.4"
        ],
        "mac": [
            "CE-FD-5D-F6-E6-A5",
            "D6-9D-3C-3F-A7-98"
        ],
        "name": "elastic-agent-46061",
        "os": {
            "family": "",
            "kernel": "6.10.14-linuxkit",
            "name": "Wolfi",
            "platform": "wolfi",
            "type": "linux",
            "version": "20230201"
        }
    },
    "input": {
        "type": "cel"
    },
    "log": {
        "origin": {
            "file": {
                "line": 878
            }
        }
    },
    "vulnerability": {
        "category": [
            "Secret"
        ],
        "description": "GENERIC_CREDS_WINDOWS_PASSWORD",
        "reference": "asd123123"
    }
}
```

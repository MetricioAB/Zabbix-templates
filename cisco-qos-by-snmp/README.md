# Cisco QOS

## Overview

Monitor Cisco QOS devices with SNMP.

## Macros Used

| Name                              | Description | Default            | Type       |
| --------------------------------- | ----------- | ------------------ | ---------- |
| {$NET.IF.IFDESCR.MATCHES}         | <p> - </p>  | `.*`               | Text macro |
| {$NET.IF.IFDESCR.NOT_MATCHES}     | <p> - </p>  | `CHANGE_IF_NEEDED` | Text macro |
| {$QOS.CLASS.MAPNAME.MATCHES}      | <p> - </p>  | `.*`               | Text macro |
| {$QOS.CLASS.MAPNAME.NOT_MATCHES}  | <p> - </p>  | `CHANGE_IF_NEEDED` | Text macro |
| {$QOS.POLICY.MAPNAME.MATCHES}     | <p> - </p>  | `.*`               | Text macro |
| {$QOS.POLICY.MAPNAME.NOT_MATCHES} | <p> - </p>  | `CHANGE_IF_NEEDED` | Text macro |

## Discovery Rules

| Name                    | Description | Type         | Key and additional info                 |
| ----------------------- | ----------- | ------------ | --------------------------------------- |
| QoS Class-Map Discovery | <p>-</p>    | `SNMP Agent` | qos.classmap.discovery<p>Update: 1h</p> |

## LLD Macros

| LLD macro                  | JSON Path                        |
| -------------------------- | -------------------------------- |
| {#CBQOSOBJECTSINDEX}       | <p>$.cbQoSObjectsIndex</p>       |
| {#CLASSMAPID}              | <p>$.classMapId</p>              |
| {#CLASSMAPNAME}            | <p>$.classMapName</p>            |
| {#HIERARCHYROLE}           | <p>$.hierarchyRole</p>           |
| {#IFALIAS}                 | <p>$.ifAlias</p>                 |
| {#IFDESCR}                 | <p>$.ifDescr</p>                 |
| {#IFINDEX}                 | <p>$.ifIndex</p>                 |
| {#PARENTCBQOSOBJECTSINDEX} | <p>$.parentCbQoSObjectsIndex</p> |
| {#POLICYDIRECTION}         | <p>$.policyDirection</p>         |
| {#POLICYMAPNAME}           | <p>$.policyMapName</p>           |
| {#QOSIFINDEX}              | <p>$.qosIfIndex</p>              |

## Items collected

| Name                                                                       | Description | Type         | Key and additional info                                                  |
| -------------------------------------------------------------------------- | ----------- | ------------ | ------------------------------------------------------------------------ |
| QoS dropped bytes by policy {#POLICYMAPNAME} using class {#CLASSMAPNAME}   | <p>-</p>    | `SNMP agent` | qos.dropped.bytes[{#QOSIFINDEX},{#CBQOSOBJECTSINDEX}]<p>Update: 5m</p>   |
| QoS dropped packets by policy {#POLICYMAPNAME} using class {#CLASSMAPNAME} | <p>-</p>    | `SNMP agent` | qos.dropped.packets[{#QOSIFINDEX},{#CBQOSOBJECTSINDEX}]<p>Update: 5m</p> |

## Triggers

| Name         | Description | Expression                                                                            | Priority |
| ------------ | ----------- | ------------------------------------------------------------------------------------- | -------- |
| Trigger name | <p>-</p>    | <p>**Expression**: last(/Host/item[{#MACRO}])<600</p><p>**Recovery expression**: </p> | warning  |

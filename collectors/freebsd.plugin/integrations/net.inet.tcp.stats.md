<!--startmeta
custom_edit_url: "https://github.com/netdata/netdata/edit/master/collectors/freebsd.plugin/integrations/net.inet.tcp.stats.md"
meta_yaml: "https://github.com/netdata/netdata/edit/master/collectors/freebsd.plugin/metadata.yaml"
sidebar_label: "net.inet.tcp.stats"
learn_status: "Published"
learn_rel_path: "Data Collection/FreeBSD"
message: "DO NOT EDIT THIS FILE DIRECTLY, IT IS GENERATED BY THE COLLECTOR'S metadata.yaml FILE"
endmeta-->

# net.inet.tcp.stats

Plugin: freebsd.plugin
Module: net.inet.tcp.stats

<img src="https://img.shields.io/badge/maintained%20by-Netdata-%2300ab44" />

## Overview

Collect overall information about TCP connections.

The plugin calls `sysctl` function to collect necessary data.

This collector is supported on all platforms.

This collector supports collecting metrics from multiple instances of this integration, including remote instances.


### Default Behavior

#### Auto-Detection

This integration doesn't support auto-detection.

#### Limits

The default configuration for this integration does not impose any limits on data collection.

#### Performance Impact

The default configuration for this integration is not expected to impose a significant performance impact on the system.


## Metrics

Metrics grouped by *scope*.

The scope defines the instance that the metric belongs to. An instance is uniquely identified by a set of labels.



### Per net.inet.tcp.stats instance

These metrics show TCP connections statistics.

This scope has no labels.

Metrics:

| Metric | Dimensions | Unit |
|:------|:----------|:----|
| ipv4.tcppackets | received, sent | packets/s |
| ipv4.tcperrors | InErrs, InCsumErrors, RetransSegs | packets/s |
| ipv4.tcphandshake | EstabResets, ActiveOpens, PassiveOpens, AttemptFails | events/s |
| ipv4.tcpconnaborts | baddata, userclosed, nomemory, timeout, linger | connections/s |
| ipv4.tcpofo | inqueue | packets/s |
| ipv4.tcpsyncookies | received, sent, failed | packets/s |
| ipv4.tcplistenissues | overflows | packets/s |
| ipv4.ecnpkts | InCEPkts, InECT0Pkts, InECT1Pkts, OutECT0Pkts, OutECT1Pkts | packets/s |



## Alerts


The following alerts are available:

| Alert name  | On metric | Description |
|:------------|:----------|:------------|
| [ 1m_ipv4_tcp_resets_sent ](https://github.com/netdata/netdata/blob/master/health/health.d/tcp_resets.conf) | ipv4.tcphandshake | average number of sent TCP RESETS over the last minute |
| [ 10s_ipv4_tcp_resets_sent ](https://github.com/netdata/netdata/blob/master/health/health.d/tcp_resets.conf) | ipv4.tcphandshake | average number of sent TCP RESETS over the last 10 seconds. This can indicate a port scan, or that a service running on this host has crashed. Netdata will not send a clear notification for this alarm. |
| [ 1m_ipv4_tcp_resets_received ](https://github.com/netdata/netdata/blob/master/health/health.d/tcp_resets.conf) | ipv4.tcphandshake | average number of received TCP RESETS over the last minute |
| [ 10s_ipv4_tcp_resets_received ](https://github.com/netdata/netdata/blob/master/health/health.d/tcp_resets.conf) | ipv4.tcphandshake | average number of received TCP RESETS over the last 10 seconds. This can be an indication that a service this host needs has crashed. Netdata will not send a clear notification for this alarm. |


## Setup

### Prerequisites

No action required.

### Configuration

#### File

The configuration file name for this integration is `netdata.conf`.
Configuration for this specific integration is located in the `[plugin:freebsd:net.inet.tcp.stats]` section within that file.

The file format is a modified INI syntax. The general structure is:

```toml
[section1]
    option 1 = some value
    option 2 = some other value

[section2]
    option 3 = some third value
```
You can edit the configuration file using the `edit-config` script from the
Netdata [config directory](https://github.com/netdata/netdata/blob/master/docs/configure/nodes.md#the-netdata-config-directory).

```bash
cd /etc/netdata 2>/dev/null || cd /opt/netdata/etc/netdata
sudo ./edit-config netdata.conf
```
#### Options



<details><summary>Config options</summary>

| Name | Description | Default | Required |
|:----|:-----------|:-------|:--------:|
| ipv4 TCP packets | Enable or disable ipv4 TCP packets metric. |  | False |
| ipv4 TCP errors | Enable or disable pv4 TCP errors metric. |  | False |
| ipv4 TCP handshake issues | Enable or disable ipv4 TCP handshake issue metric. |  | False |
| TCP connection aborts | Enable or disable TCP connection aborts metric. |  | False |
| TCP out-of-order queue | Enable or disable TCP out-of-order queue metric. |  | False |
| TCP SYN cookies | Enable or disable TCP SYN cookies metric. |  | False |
| TCP listen issues | Enable or disable TCP listen issues metric. |  | False |
| ECN packets | Enable or disable ECN packets metric. |  | False |

</details>

#### Examples
There are no configuration examples.


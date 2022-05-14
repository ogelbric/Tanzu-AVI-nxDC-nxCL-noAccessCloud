# Tanzu-AVI-nxDC-nxCL-noAccessCloud

This write up will center on the setup of vCenter with AVI enabling several vCenter Data Centers and vCenter Clusters with WCP (Tanzu TKGs). 
AVI in "No Access Mode" (https://avinetworks.com/docs/21.1/installing-avi-vantage-for-vmware-vcenter/#deploying-avi-vantage-in-read-and-no-access-mode)

## In the beginning the inspiration:

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/inspiration.png)

Lets go into more detail: 

vCenter 7u3d required (Marker enablement! Default Cloud and Marker selected attached vip pools) 
The various versions (to avoind confusion): 

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/vcenterversions.png)

AVI Verision used (controller-21.1.2-9124) 

The vCenter setup with 2 DC's and 3 CL's and 2 CL's in one DC and one CL in one DC

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/setup1.png)

The vCenter network setup: 

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/networksetup1.png)

### General Setup Steps

Deploy AVI controller
Doploy AVI SE's (my case 3x2) in the DC's/CL's
Connect the SE's to the networks
Deploy Marker (PDF below) 
![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/1061720785_9851830dbba540b5b54b26daf9329690-040522-1117-3444.pdf)

# Enable WCP in 2 x DC and 3 x CL

## Lets get Started

# Network Information
```
AVI = 192.168.3.40

AVI SE1 DC-a / cl-aa = 192.168.3.41
AVI SE2 DC-a / cl-aa = 192.168.3.42

AVI SE1 DC-a / cl-ab = 192.168.1.41
AVI SE2 DC-a / cl-ab = 192.168.1.42

AVI SE1 DC-b / cl-ba = 192.168.2.41
AVI SE2 DC-b / cl-bb = 192.168.2.42


vCenter = 192.168.3.50
DNS = 10.197.79.7
NTP = 10.128.152.81

dc-a / cl-aa / SE1
MGT = 192.168.3.x     Net Adapter 1  05:17 eth0
Work = 192.168.5.x    Net Adapter 2  50:88 eth3 5.41
Front = 192.168.7.x   Net Adapter 3  5a:4b eth4 7.41

dc-a / cl-aa / SE2
MGT = 192.168.3.x     Net Adapter 1  85:34 eth0
Work = 192.168.5.x    Net Adapter 2  dc:1d eth3 5.42
Front = 192.168.7.x   Net Adapter 3  b4:b2 eth4 7.42


dc-a / cl-ab / SE1
MGT = 192.168.1.x     Net Adapter 1  04:4e eth0
Work = 192.168.4.x    Net Adapter 2  8c:a0 eth3 4.41
Front = 192.168.6.x   Net Adapter 3  b4:f7 eth4 6.41

dc-a / cl-ab / SE2
MGT = 192.168.1.x     Net Adapter 1  eb:a2 eth0
Work = 192.168.4.x    Net Adapter 2  41:f4 eth3 4.42
Front = 192.168.6.x   Net Adapter 3  39:db eth4 6.42

dc-b / cl-ba / SE1
MGT = 192.168.2.x     Net Adapter 1  59:91 eth0
Work = 192.168.8.x    Net Adapter 2  30:79 eth3 8.41
Front = 192.168.9.x   Net Adapter 3  28:8a eth4 9.41

dc-b / cl-ba / SE2
MGT = 192.168.2.x     Net Adapter 1  73:64 eth0
Work = 192.168.8.x    Net Adapter 2  3a:f7 eth3 8.42
Front = 192.168.9.x   Net Adapter 3  53:81 eth4 9.42

```



# AVI Controller OVA Deployment 

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/avicontrollerovadeployment.png)

# Power on AVI Controller

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/PowerOnAVI.png)

# Log on to AVI for the first time

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/LogOnFirstTime.png)

# Answer some basic questions

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/AVI1.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/AVI2.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/AVI3.png)

# Generate Key for SE's and AVI Controller image:

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/AVIKeyGen1.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/AVIKeyGen2.png)

```
Cluster UUID: cluster-6a0818c4-4ab1-47f3-a162-99c9581cba42
```

AVI SE's OVA needs to be updated with the AVI controller UUID

# Generate AVI SE OVA 

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/AVISEImage.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/AVISEdownload.png)


# Power on AVI SE in dc-a / cl-a

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/AVISE1.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/AVISE2.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/AVISE3.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/AVISE4.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/AVISE5.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/AVISE6.png)

# Check AVI SE 1 in AVI Controller

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/AVISE1up.png)


# Deploy AVI SE 2 for dc-a and cl-a

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/AVISE22.png)

# Check AVI SE 2 in AVI Controller

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/AVISE2up.png)

# Create some SE groups and move the SE's into that group 

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/AVSEgroups123.png)

# Match up the MAC's and interfaces 

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/NetMatchdcacla1.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/NetMatchdcacla2.png)

# Put IP's onto both SE interfaces

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/IPSEdcaclaa1.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/IPSEdcaclaa2.png)

# Routing from workload to Front end network

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/Route1.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/Route2.png)

# Frontend Network Declaration / Pool / Adding pool to Default Cloud 

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/FrontNetwork1.png)
![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/FrontNetwork2.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/FrontPool1.png)
![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/FrontPool2.png)
![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/FrontPool3.png)
![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/DefCloud1.png)
![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/DefCloud2.png)

# Collecting some ID's 

```
PS C:\Users\Administrator> $vcenter = Connect-VIServer 192.168.3.50 -User administrator@vsphere.local -Password "VMware1!"
PS C:\Users\Administrator> $vcenter.InstanceUuid

7aefe7fe-10bd-4a1e-a9c7-a92227e40298


PS C:\Users\Administrator> get-cluster

Name                           HAEnabled  HAFailover DrsEnabled DrsAutomationLevel
                                          Level
----                           ---------  ---------- ---------- ------------------
cl-ba                          True       1          True       FullyAutomated
cl-ab                          True       1          True       FullyAutomated
cl-aa                          True       1          True       FullyAutomated


PS C:\Users\Administrator> get-cluster cl-aa | select ID

Id
--
ClusterComputeResource-domain-c8

PS C:\Users\Administrator> get-cluster cl-ab | select ID

Id
--
ClusterComputeResource-domain-c79

PS C:\Users\Administrator> get-cluster cl-ba | select ID

Id
--
ClusterComputeResource-domain-c40


Marker creation:
==============
 
Marker for cl-aa = domain-c8:7aefe7fe-10bd-4a1e-a9c7-a92227e40298
Marker for cl-ab = domain-c79:7aefe7fe-10bd-4a1e-a9c7-a92227e40298
Marker for cl-ba = domain-c40:7aefe7fe-10bd-4a1e-a9c7-a92227e40298

```

# Marker Creation on AVI controller

```
[root@orfdns ~]# ssh admin@192.168.3.40
Avi Cloud Controller
Avi Networks software, Copyright (C) 2013-2017 by Avi Networks, Inc.
All rights reserved. 
Management:   192.168.3.40/24                UP 
Gateway:      192.168.3.1                    UP 


admin@192-168-3-40:~$ shell
Login: admin
Password: 

[admin:192-168-3-40]: > 
[admin:192-168-3-40]: > show serviceenginegroup
+---------------+---------------------------------------------------------+---------------+
| Name          | UUID                                                    | Cloud         |
+---------------+---------------------------------------------------------+---------------+
| Default-Group | serviceenginegroup-82201162-f8c7-4345-9f2f-d879521ff0c9 | Default-Cloud |
| dc-a-cl-aa    | serviceenginegroup-a5d9e72d-9597-41ce-ab09-46bb1ea8a27d | Default-Cloud |
| dc-b-cl-ba    | serviceenginegroup-25d76c26-3d4b-451a-9685-34e052486a77 | Default-Cloud |
| dc-a-cl-ab    | serviceenginegroup-008123f1-dd98-47c4-9231-02aff2f596a4 | Default-Cloud |
+---------------+---------------------------------------------------------+---------------+
[admin:192-168-3-40]: > configure serviceenginegroup dc-a-cl-aa
Updating an existing object. Currently, the object is:
+-----------------------------------------+---------------------------------------------------------+
| Field                                   | Value                                                   |
+-----------------------------------------+---------------------------------------------------------+
| uuid                                    | serviceenginegroup-a5d9e72d-9597-41ce-ab09-46bb1ea8a27d |
| name                                    | dc-a-cl-aa                                              |
| max_vs_per_se                           | 10                                                      |
.
.
.
| log_agent_log_storage_min_sz            | 1024 mb                                                 |
| log_message_max_file_list_size          | 64                                                      |
+-----------------------------------------+---------------------------------------------------------+
[admin:192-168-3-40]: serviceenginegroup> markers
New object being created
[admin:192-168-3-40]: serviceenginegroup:markers> key clustername
[admin:192-168-3-40]: serviceenginegroup:markers> values domain-c8:7aefe7fe-10bd-4a1e-a9c7-a92227e40298
[admin:192-168-3-40]: serviceenginegroup:markers> save
s[admin:192-168-3-40]: serviceenginegroup> save
+-----------------------------------------+---------------------------------------------------------+
| Field                                   | Value                                                   |
+-----------------------------------------+---------------------------------------------------------+
| uuid                                    | serviceenginegroup-a5d9e72d-9597-41ce-ab09-46bb1ea8a27d |
| name                                    | dc-a-cl-aa                                              |
| max_vs_per_se                           | 10                                                      |
| min_scaleout_per_vs                     | 1                                                       |
.
.
.
| log_message_max_file_list_size          | 64                                                      |
| markers[1]                              |                                                         |
|   key                                   | clustername                                             |
|   values[1]                             | domain-c8:7aefe7fe-10bd-4a1e-a9c7-a92227e40298          |
+-----------------------------------------+---------------------------------------------------------+
[admin:192-168-3-40]: >
```

Marker on Network object

```
[admin:192-168-3-40]: > show network
+---------------------+----------------------------------------------+
| Name                | UUID                                         |
+---------------------+----------------------------------------------+
| frontend-dc-a-cl-aa | network-b66a7edc-b07a-4431-ab77-a415cca0e9c4 |
+---------------------+----------------------------------------------+
[admin:192-168-3-40]: > configure network 
Usage: 'configure network <name>'. You must enter the object name.
[admin:192-168-3-40]: > configure network frontend-dc-a-cl-aa
Updating an existing object. Currently, the object is:
+----------------------------+----------------------------------------------+
| Field                      | Value                                        |
+----------------------------+----------------------------------------------+
| uuid                       | network-b66a7edc-b07a-4431-ab77-a415cca0e9c4 |
| name                       | frontend-dc-a-cl-aa                          |
| vcenter_dvs                | True                                         |
| dhcp_enabled               | True                                         |
| exclude_discovered_subnets | False                                        |
| configured_subnets[1]      |                                              |
|   prefix                   | 192.168.7.0/24                               |
|   static_ip_ranges[1]      |                                              |
|     range                  |                                              |
|       begin                | 192.168.7.50                                 |
|       end                  | 192.168.7.100                                |
|     type                   | STATIC_IPS_FOR_VIP_AND_SE                    |
| vrf_context_ref            | global                                       |
| synced_from_se             | False                                        |
| ip6_autocfg_enabled        | True                                         |
| tenant_ref                 | admin                                        |
| cloud_ref                  | Default-Cloud                                |
+----------------------------+----------------------------------------------+
[admin:192-168-3-40]: network> markers
New object being created
[admin:192-168-3-40]: network:markers> key clustername
[admin:192-168-3-40]: network:markers> values domain-c8:7aefe7fe-10bd-4a1e-a9c7-a92227e40298
[admin:192-168-3-40]: network:markers> save
[admin:192-168-3-40]: network> save
+----------------------------+------------------------------------------------+
| Field                      | Value                                          |
+----------------------------+------------------------------------------------+
| uuid                       | network-b66a7edc-b07a-4431-ab77-a415cca0e9c4   |
| name                       | frontend-dc-a-cl-aa                            |
| vcenter_dvs                | True                                           |
| dhcp_enabled               | True                                           |
| exclude_discovered_subnets | False                                          |
| configured_subnets[1]      |                                                |
|   prefix                   | 192.168.7.0/24                                 |
|   static_ip_ranges[1]      |                                                |
|     range                  |                                                |
|       begin                | 192.168.7.50                                   |
|       end                  | 192.168.7.100                                  |
|     type                   | STATIC_IPS_FOR_VIP_AND_SE                      |
| vrf_context_ref            | global                                         |
| synced_from_se             | False                                          |
| ip6_autocfg_enabled        | True                                           |
| markers[1]                 |                                                |
|   key                      | clustername                                    |
|   values[1]                | domain-c8:7aefe7fe-10bd-4a1e-a9c7-a92227e40298 |
| tenant_ref                 | admin                                          |
| cloud_ref                  | Default-Cloud                                  |
+----------------------------+------------------------------------------------+
[admin:192-168-3-40]: > 
```

# Check the profiles :

```
[admin:192-168-3-40]: > show ipamdnsproviderprofile
+----------------+-------------------------------------------------------------+
| Name           | UUID                                                        |
+----------------+-------------------------------------------------------------+
| ipam-dc-a-cl-a | ipamdnsproviderprofile-34e6d3e9-b1e6-4af0-9f5d-f29a74036798 |
+----------------+-------------------------------------------------------------+
[admin:192-168-3-40]: > show ipamdnsproviderprofile ipam-dc-a-cl-a
+-------------------------+-------------------------------------------------------------+
| Field                   | Value                                                       |
+-------------------------+-------------------------------------------------------------+
| uuid                    | ipamdnsproviderprofile-34e6d3e9-b1e6-4af0-9f5d-f29a74036798 |
| name                    | ipam-dc-a-cl-a                                              |
| type                    | IPAMDNS_TYPE_INTERNAL                                       |
| internal_profile        |                                                             |
|   ttl                   | 30 sec                                                      |
|   usable_networks[1]    |                                                             |
|     nw_ref              | frontend-dc-a-cl-aa                                         |
| gcp_profile             |                                                             |
|   match_se_group_subnet | False                                                       |
|   use_gcp_network       | False                                                       |
| azure_profile           |                                                             |
|   use_enhanced_ha       | False                                                       |
|   use_standard_alb      | False                                                       |
| allocate_ip_in_vrf      | False                                                       |
| tenant_ref              | admin                                                       |
+-------------------------+-------------------------------------------------------------+
[admin:192-168-3-40]: > 
```
# Cert creation

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/cert1.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/cert2.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/cert3.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/cert4.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/cert5.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/cert6.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/cert7.png)


```
-----BEGIN CERTIFICATE-----
MIIC0TCCAbmgAwIBAgIUPr0/kIqZVTSbztzjygQk21vqYxYwDQYJKoZIhvcNAQEL
BQAwGDEWMBQGA1UEAwwNYXZpLmxhYi5sb2NhbDAeFw0yMjA1MTEyMTU0MzRaFw0y
MzA1MTEyMTU0MzRaMBgxFjAUBgNVBAMMDWF2aS5sYWIubG9jYWwwggEiMA0GCSqG
SIb3DQEBAQUAA4IBDwAwggEKAoIBAQC+8rEs7kDV0GLVPMYfBo0H/Z+IfvLemWRz
QTEFrmwAMZfQib6Trhz5QTO+Uh/YaTiQ/4P7fFF/h00+xmfa5OAoVu+LMZnpubTb
2L5Q7HMZCgNLxn0iunL/VOgbIPe/cOAtwaKcm2mYeQYr8PshC8CZX7hTTqJ+RlgH
OjS4qhCWanmDaGgqwwgWEIoFhgyz1GrMzcKLA7H4I88FP/Ej5ksWHPiuB8FV4oTR
Ge5nFV2sDwqAe1AaO5Xtpd4TxMrxTCpnm/osPv5qVjKInOzEsuc+CeWNmP0kl8mP
AMmBKDsvqTkxUX5J+0VS/daET9fDxxXWiWaHu12mjxc8qYUu3ExVAgMBAAGjEzAR
MA8GA1UdEQQIMAaHBMCoAygwDQYJKoZIhvcNAQELBQADggEBAFoaDD9EB9EqLqbc
HjqLJxGCKe+admsGVz3vrP7EoRgfiB0Cna4muPC7d+HBvEe2aE3fPLKQ737NqZoi
7P6A8t4CSrz/0yN1X5WWKiBj+VmoTnlLLpNR703BF5Uhsx+VmQoxVo5TLR9JDJyD
zq6v3jHTDBlFv237/Niv3zg19noOLjTQYdAYeGLbxb0Bw2PshpSKqGOIAMHK5A2q
jHiC2fAmca1/bRY/2eLhmg/okMKc/EXWZTlOCHEVtgHyKZiRM5vtcyuSuSnwa1qK
50jQrYncWVjP1fc2N8A58Yy/EUUwJaFYIeD5LWllzj1jeDXGApPVsEkQ+pLG4TDQ
q+JPGx4=
-----END CERTIFICATE-----
```

# Enable WCP in vCenter

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/wcp1.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/wcp2.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/wcp3.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/wcp4.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/wcp5.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/wcp6.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/wcp7.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/wcp8.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/wcp9.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/wcp10.png)

# Cloud 1 is green

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/Green1.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/Green2.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/Green3.png)


# Configuring Service Engine Group Markers DC a / CL ab and DC b / CL aa

```
[admin:192-168-3-40]: > 
[admin:192-168-3-40]: > show serviceenginegroup
+---------------+---------------------------------------------------------+---------------+
| Name          | UUID                                                    | Cloud         |
+---------------+---------------------------------------------------------+---------------+
| Default-Group | serviceenginegroup-82201162-f8c7-4345-9f2f-d879521ff0c9 | Default-Cloud |
| dc-a-cl-aa    | serviceenginegroup-a5d9e72d-9597-41ce-ab09-46bb1ea8a27d | Default-Cloud |
| dc-b-cl-ba    | serviceenginegroup-25d76c26-3d4b-451a-9685-34e052486a77 | Default-Cloud |
| dc-a-cl-ab    | serviceenginegroup-008123f1-dd98-47c4-9231-02aff2f596a4 | Default-Cloud |
+---------------+---------------------------------------------------------+---------------+
[admin:192-168-3-40]: > configure serviceenginegroup dc-a-cl-ab
Updating an existing object. Currently, the object is:
+-----------------------------------------+---------------------------------------------------------+
| Field                                   | Value                                                   |
+-----------------------------------------+---------------------------------------------------------+
| uuid                                    | serviceenginegroup-008123f1-dd98-47c4-9231-02aff2f596a4 |
| name                                    | dc-a-cl-ab                                              |
| max_vs_per_se                           | 10                                                      |
.
.
.
| log_agent_log_storage_min_sz            | 1024 mb                                                 |
| log_message_max_file_list_size          | 64                                                      |
+-----------------------------------------+---------------------------------------------------------+
[admin:192-168-3-40]: serviceenginegroup> markers
New object being created
[admin:192-168-3-40]: serviceenginegroup:markers> key clustername
[admin:192-168-3-40]: serviceenginegroup:markers> values domain-c79:7aefe7fe-10bd-4a1e-a9c7-a92227e40298
[admin:192-168-3-40]: serviceenginegroup:markers> save
sav[admin:192-168-3-40]: serviceenginegroup> save
+-----------------------------------------+---------------------------------------------------------+
| Field                                   | Value                                                   |
+-----------------------------------------+---------------------------------------------------------+
| uuid                                    | serviceenginegroup-008123f1-dd98-47c4-9231-02aff2f596a4 |
| name                                    | dc-a-cl-ab                                              |
| max_vs_per_se                           | 10                                                      |
.
.
.
| markers[1]                              |                                                         |
|   key                                   | clustername                                             |
|   values[1]                             | domain-c79:7aefe7fe-10bd-4a1e-a9c7-a92227e40298         |
+-----------------------------------------+---------------------------------------------------------+
[admin:192-168-3-40]: > configure serviceenginegroup dc-b-cl-ba
Updating an existing object. Currently, the object is:
+-----------------------------------------+---------------------------------------------------------+
| Field                                   | Value                                                   |
+-----------------------------------------+---------------------------------------------------------+
| uuid                                    | serviceenginegroup-25d76c26-3d4b-451a-9685-34e052486a77 |
| name                                    | dc-b-cl-ba                                              |
| max_vs_per_se                           | 10                                                      |
.
.
.
| log_agent_log_storage_min_sz            | 1024 mb                                                 |
| log_message_max_file_list_size          | 64                                                      |
+-----------------------------------------+---------------------------------------------------------+
[admin:192-168-3-40]: serviceenginegroup> markers
New object being created
[admin:192-168-3-40]: serviceenginegroup:markers> key clustername
[admin:192-168-3-40]: serviceenginegroup:markers> values domain-c40:7aefe7fe-10bd-4a1e-a9c7-a92227e40298
[admin:192-168-3-40]: serviceenginegroup:markers> save
sa[admin:192-168-3-40]: serviceenginegroup> save
+-----------------------------------------+---------------------------------------------------------+
| Field                                   | Value                                                   |
+-----------------------------------------+---------------------------------------------------------+
| uuid                                    | serviceenginegroup-25d76c26-3d4b-451a-9685-34e052486a77 |
| name                                    | dc-b-cl-ba                                              |
| max_vs_per_se                           | 10                                                      |
.
.
.
| log_message_max_file_list_size          | 64                                                      |
| markers[1]                              |                                                         |
|   key                                   | clustername                                             |
|   values[1]                             | domain-c40:7aefe7fe-10bd-4a1e-a9c7-a92227e40298         |
+-----------------------------------------+---------------------------------------------------------+
[admin:192-168-3-40]: > 
```

# AVI SE1/2 DC a / CL ab OVA deployment

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/AVISEab1.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/AVISEab2.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/AVISEAB3.png)

Then power on SE's in DC a / CL ab

# 2 more SE's in the AVI controller

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/AVIController2moreses.png)

# Move new SE's to dc-a-cl-ab Service Engine Group and apply .4 and .6 IPs to matching interfaces (see chart above) 

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/AVISE3-4-1.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/AVISE3-4-2.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/AVISE3-4-3.png)

# Frontend network for dc-a cl-ab and route 

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/AVIFrontenddcaclab1.png)
![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/AVIFRontenddcaclab2.png)
![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/AVIRoutedcaclab1.png)

# Add marker to dc-a cl-ab network frontend

```
[admin:192-168-3-40]: > show network
+---------------------+----------------------------------------------+
| Name                | UUID                                         |
+---------------------+----------------------------------------------+
| frontend-dc-a-cl-aa | network-b66a7edc-b07a-4431-ab77-a415cca0e9c4 |
| frontend-dc-a-cl-ab | network-9b588dd0-16c4-4e7a-a5d0-173dffe81ec7 |
+---------------------+----------------------------------------------+
[admin:192-168-3-40]: > configure network frontend-dc-a-cl-ab
Updating an existing object. Currently, the object is:
+----------------------------+----------------------------------------------+
| Field                      | Value                                        |
+----------------------------+----------------------------------------------+
| uuid                       | network-9b588dd0-16c4-4e7a-a5d0-173dffe81ec7 |
| name                       | frontend-dc-a-cl-ab                          |
| vcenter_dvs                | True                                         |
| dhcp_enabled               | True                                         |
| exclude_discovered_subnets | False                                        |
| configured_subnets[1]      |                                              |
|   prefix                   | 192.168.6.0/24                               |
|   static_ip_ranges[1]      |                                              |
|     range                  |                                              |
|       begin                | 192.168.6.50                                 |
|       end                  | 192.168.6.100                                |
|     type                   | STATIC_IPS_FOR_VIP_AND_SE                    |
| vrf_context_ref            | global                                       |
| synced_from_se             | False                                        |
| ip6_autocfg_enabled        | True                                         |
| tenant_ref                 | admin                                        |
| cloud_ref                  | Default-Cloud                                |
+----------------------------+----------------------------------------------+
[admin:192-168-3-40]: network> markers
New object being created
[admin:192-168-3-40]: network:markers> key clustername
[admin:192-168-3-40]: network:markers> values domain-c79:7aefe7fe-10bd-4a1e-a9c7-a92227e40298
[admin:192-168-3-40]: network:markers> save
sav[admin:192-168-3-40]: network> save
+----------------------------+-------------------------------------------------+
| Field                      | Value                                           |
+----------------------------+-------------------------------------------------+
| uuid                       | network-9b588dd0-16c4-4e7a-a5d0-173dffe81ec7    |
| name                       | frontend-dc-a-cl-ab                             |
| vcenter_dvs                | True                                            |
| dhcp_enabled               | True                                            |
| exclude_discovered_subnets | False                                           |
| configured_subnets[1]      |                                                 |
|   prefix                   | 192.168.6.0/24                                  |
|   static_ip_ranges[1]      |                                                 |
|     range                  |                                                 |
|       begin                | 192.168.6.50                                    |
|       end                  | 192.168.6.100                                   |
|     type                   | STATIC_IPS_FOR_VIP_AND_SE                       |
| vrf_context_ref            | global                                          |
| synced_from_se             | False                                           |
| ip6_autocfg_enabled        | True                                            |
| markers[1]                 |                                                 |
|   key                      | clustername                                     |
|   values[1]                | domain-c79:7aefe7fe-10bd-4a1e-a9c7-a92227e40298 |
| tenant_ref                 | admin                                           |
| cloud_ref                  | Default-Cloud                                   |
+----------------------------+-------------------------------------------------+
[admin:192-168-3-40]: > 
```
# Add the new Usable Network to the default cloud IPAM 

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/AVIADDUsableNetwork2.png)

# Check the profiles if aa and ab are attached 

```
[admin:192-168-3-40]: > 
[admin:192-168-3-40]: > show ipamdnsproviderprofile
+----------------+-------------------------------------------------------------+
| Name           | UUID                                                        |
+----------------+-------------------------------------------------------------+
| ipam-dc-a-cl-a | ipamdnsproviderprofile-34e6d3e9-b1e6-4af0-9f5d-f29a74036798 |
+----------------+-------------------------------------------------------------+

[admin:192-168-3-40]: > 
[admin:192-168-3-40]: > 
[admin:192-168-3-40]: > 
[admin:192-168-3-40]: > show ipamdnsproviderprofile ipam-dc-a-cl-a
+-------------------------+-------------------------------------------------------------+
| Field                   | Value                                                       |
+-------------------------+-------------------------------------------------------------+
| uuid                    | ipamdnsproviderprofile-34e6d3e9-b1e6-4af0-9f5d-f29a74036798 |
| name                    | ipam-dc-a-cl-a                                              |
| type                    | IPAMDNS_TYPE_INTERNAL                                       |
| internal_profile        |                                                             |
|   ttl                   | 30 sec                                                      |
|   usable_networks[1]    |                                                             |
|     nw_ref              | frontend-dc-a-cl-aa                                         |
|   usable_networks[2]    |                                                             |
|     nw_ref              | frontend-dc-a-cl-ab                                         |
| gcp_profile             |                                                             |
|   match_se_group_subnet | False                                                       |
|   use_gcp_network       | False                                                       |
| azure_profile           |                                                             |
|   use_enhanced_ha       | False                                                       |
|   use_standard_alb      | False                                                       |
| allocate_ip_in_vrf      | False                                                       |
| tenant_ref              | admin                                                       |
+-------------------------+-------------------------------------------------------------+
[admin:192-168-3-40]: > 
```

# WCP Enableent for DC a / CL ab

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/WCPEnablement2-1.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/WCPEnablement2-2.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/WCPEnablement2-3.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/WCPEnablement2-4.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/WCPEnablement2-5.png)

# WCP is enabled in DC a CL AB

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/WCP2Enableddcaclab1.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/WCP2Enableddcaclab2.png)


# Deployment of SE's in DC b and CL ba OVA

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/AVISEba11.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/AVISEba12.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/AVISEba13.png)

Power on OVA's

# SE's in AVI controller move to SE group

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/AVIse3g1.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/AVIse3g2.png)

# Set up networks

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/AVINetdcbclba1.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/AVINetdcbclba2.png)


# Frontend network for DC b CL ba and route

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/AVIf3net-1.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/AVIf3net-2.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/AVIf3net-3.png)



# Add marker for frontend network for DC b / CL ab

```
[admin:192-168-3-40]: > 
[admin:192-168-3-40]: > show network
+---------------------+----------------------------------------------+
| Name                | UUID                                         |
+---------------------+----------------------------------------------+
| frontend-dc-a-cl-aa | network-b66a7edc-b07a-4431-ab77-a415cca0e9c4 |
| frontend-dc-a-cl-ab | network-9b588dd0-16c4-4e7a-a5d0-173dffe81ec7 |
| frontend-dc-b-cl-ba | network-79d13a9d-a291-444a-b7d1-8291929e266c |
+---------------------+----------------------------------------------+
[admin:192-168-3-40]: > configure network frontend-dc-b-cl-ba
Updating an existing object. Currently, the object is:
+----------------------------+----------------------------------------------+
| Field                      | Value                                        |
+----------------------------+----------------------------------------------+
| uuid                       | network-79d13a9d-a291-444a-b7d1-8291929e266c |
| name                       | frontend-dc-b-cl-ba                          |
| vcenter_dvs                | True                                         |
| dhcp_enabled               | True                                         |
| exclude_discovered_subnets | False                                        |
| configured_subnets[1]      |                                              |
|   prefix                   | 192.168.9.0/24                               |
|   static_ip_ranges[1]      |                                              |
|     range                  |                                              |
|       begin                | 192.168.9.50                                 |
|       end                  | 192.168.9.100                                |
|     type                   | STATIC_IPS_FOR_VIP_AND_SE                    |
| vrf_context_ref            | global                                       |
| synced_from_se             | False                                        |
| ip6_autocfg_enabled        | True                                         |
| tenant_ref                 | admin                                        |
| cloud_ref                  | Default-Cloud                                |
+----------------------------+----------------------------------------------+
[admin:192-168-3-40]: network> markers
New object being created
[admin:192-168-3-40]: network:markers> 
[admin:192-168-3-40]: network:markers> key clustername
[admin:192-168-3-40]: network:markers> values domain-c40:7aefe7fe-10bd-4a1e-a9c7-a92227e40298
[admin:192-168-3-40]: network:markers> save
s[admin:192-168-3-40]: network> save
+----------------------------+-------------------------------------------------+
| Field                      | Value                                           |
+----------------------------+-------------------------------------------------+
| uuid                       | network-79d13a9d-a291-444a-b7d1-8291929e266c    |
| name                       | frontend-dc-b-cl-ba                             |
| vcenter_dvs                | True                                            |
| dhcp_enabled               | True                                            |
| exclude_discovered_subnets | False                                           |
| configured_subnets[1]      |                                                 |
|   prefix                   | 192.168.9.0/24                                  |
|   static_ip_ranges[1]      |                                                 |
|     range                  |                                                 |
|       begin                | 192.168.9.50                                    |
|       end                  | 192.168.9.100                                   |
|     type                   | STATIC_IPS_FOR_VIP_AND_SE                       |
| vrf_context_ref            | global                                          |
| synced_from_se             | False                                           |
| ip6_autocfg_enabled        | True                                            |
| markers[1]                 |                                                 |
|   key                      | clustername                                     |
|   values[1]                | domain-c40:7aefe7fe-10bd-4a1e-a9c7-a92227e40298 |
| tenant_ref                 | admin                                           |
| cloud_ref                  | Default-Cloud                                   |
+----------------------------+-------------------------------------------------+
[admin:192-168-3-40]: 
```
# Add dc b cl ba frontend network to IPAM profile 

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/AVIIpam3.png)

# Check to make sure the new profile is attached

```
[admin:192-168-3-40]: > show ipamdnsproviderprofile
+----------------+-------------------------------------------------------------+
| Name           | UUID                                                        |
+----------------+-------------------------------------------------------------+
| ipam-dc-a-cl-a | ipamdnsproviderprofile-34e6d3e9-b1e6-4af0-9f5d-f29a74036798 |
+----------------+-------------------------------------------------------------+
[admin:192-168-3-40]: > 
[admin:192-168-3-40]: > show ipamdnsproviderprofile 
[admin:192-168-3-40]: > show ipamdnsproviderprofile ipam-dc-a-cl-a
+-------------------------+-------------------------------------------------------------+
| Field                   | Value                                                       |
+-------------------------+-------------------------------------------------------------+
| uuid                    | ipamdnsproviderprofile-34e6d3e9-b1e6-4af0-9f5d-f29a74036798 |
| name                    | ipam-dc-a-cl-a                                              |
| type                    | IPAMDNS_TYPE_INTERNAL                                       |
| internal_profile        |                                                             |
|   ttl                   | 30 sec                                                      |
|   usable_networks[1]    |                                                             |
|     nw_ref              | frontend-dc-a-cl-aa                                         |
|   usable_networks[2]    |                                                             |
|     nw_ref              | frontend-dc-a-cl-ab                                         |
|   usable_networks[3]    |                                                             |
|     nw_ref              | frontend-dc-b-cl-ba                                         |
| gcp_profile             |                                                             |
|   match_se_group_subnet | False                                                       |
|   use_gcp_network       | False                                                       |
| azure_profile           |                                                             |
|   use_enhanced_ha       | False                                                       |
|   use_standard_alb      | False                                                       |
| allocate_ip_in_vrf      | False                                                       |
| tenant_ref              | admin                                                       |
+-------------------------+-------------------------------------------------------------+
[admin:192-168-3-40]: > 
```



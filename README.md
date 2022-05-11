# Tanzu-AVI-nxDC-nxCL-noAccessCloud

This write up will center on the setup of vCenter with AVI enabling several vCenter Data Centers and vCenter Clusters with WCP (Tanzu TKGs). 
AVI in "No Access Mode" (https://avinetworks.com/docs/21.1/installing-avi-vantage-for-vmware-vcenter/#deploying-avi-vantage-in-read-and-no-access-mode)

## In the beginning the inspiration:

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/inspiration.png)

Lets go into more detail: 

vCenter 7u3d required (Marker enablement!) 
The various versions (to avoind confusion): 

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/vcenterversions.png)

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

Enable WCP in 2 x DC and 3 x CL

## Lets get Started

# Network Information
```
AVI = 192.168.3.40

AVI SE1 DC-a / cl-aa = 192.168.3.41
AVI SE2 DC-a / cl-aa = 192.168.3.42

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


```



# AVI Controller OVA Deployment 

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/avicontrollerovadeployment.png)

Power on AVI Controller

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/PowerOnAVI.png)

Log on to AVI for the first time

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/LogOnFirstTime.png)

Answer some basic questions

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/AVI1.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/AVI2.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/AVI3.png)

Generate Key for SE's and AVI Controller image:

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/AVIKeyGen1.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/AVIKeyGen2.png)

```
Cluster UUID: cluster-6a0818c4-4ab1-47f3-a162-99c9581cba42
```

AVI SE's OVA needs to be updated with the AVI controller UUID

Generate AVI SE OVA 

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/AVISEImage.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/AVISEdownload.png)


Power on AVI SE in dc-a / cl-a

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/AVISE1.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/AVISE2.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/AVISE3.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/AVISE4.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/AVISE5.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/AVISE6.png)

Check AVI SE 1 in AVI Controller

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/AVISE1up.png)


Deploy AVI SE 2 for dc-a and cl-a

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/AVISE22.png)

Check AVI SE 2 in AVI Controller

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/AVISE2up.png)

Create som SE groups and move the SE's into that group 

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/SEGroupsAndSeMoved1.png)

Match up the MAC's and interfaces 

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/NetMatchdcacla1.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/NetMatchdcacla2.png)

Put IP's onto both SE interfaces

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/IPSEdcaclaa1.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/IPSEdcaclaa2.png)

Routing from workload to Front end network

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/Route1.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/Route2.png)

Frontend Network Declaration / Pool / Adding pool to Default Cloud 

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/FrontNetwork1.png)
![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/FrontNetwork2.png)

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/FrontPool1.png)
![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/FrontPool2.png)
![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/FrontPool3.png)
![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/DefCloud1.png)
![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/DefCloud2.png)

Collecting some ID's 

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

Marker Creation on AVI controller

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

[admin:192-168-3-40]: > show serviceenginegroup
+---------------+---------------------------------------------------------+---------------+
| Name          | UUID                                                    | Cloud         |
+---------------+---------------------------------------------------------+---------------+
| Default-Group | serviceenginegroup-82201162-f8c7-4345-9f2f-d879521ff0c9 | Default-Cloud |
| dc-a-cl-aa    | serviceenginegroup-a5d9e72d-9597-41ce-ab09-46bb1ea8a27d | Default-Cloud |
| dc-a-cl-ab    | serviceenginegroup-20bf478c-3d0f-4c3a-84ef-b40284bdf2cd | Default-Cloud |
| dc-b-cl-aa    | serviceenginegroup-25d76c26-3d4b-451a-9685-34e052486a77 | Default-Cloud |
+---------------+---------------------------------------------------------+---------------+
[admin:192-168-3-40]: > 
```




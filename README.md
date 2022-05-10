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

AVI = 192.168.3.40
vCenter = 192.168.3.50

DNS = 10.197.79.7
NTP = 10.128.152.81




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

Cluster UUID: cluster-6a0818c4-4ab1-47f3-a162-99c9581cba42






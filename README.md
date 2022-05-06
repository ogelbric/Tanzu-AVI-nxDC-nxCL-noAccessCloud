# Tanzu-AVI-nxDC-nxCL-noAccessCloud

This write up wil center on the setup of vCenter with AVI and enabling several vCenter Data Centers and vCenter Clusters with WCP (Tanzu TKGs). 

## In the beginning was the inspiration:

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/inspiration.png)

Lets go into more detail: 

vCenter 7u3d is needed (Marker enablement!) 
Here are the various versions (to avoind confusion): 

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/vcenterversions.png)

Here is the vCenter setup with 2 DC's and 3 CL's and 2 CL's in one DC and one CL in one DC

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/setup1.png)

Here is the vCenter network setup: 

![Version](https://github.com/ogelbric/Tanzu-AVI-nxDC-nxCL-noAccessCloud/blob/main/networksetup1.png)

## General Setup Steps

Deploy AVI controller
Doploy AVI SE's (my case 3x2) in the DC's/CL's
Connect the SE's to the networks
Deploy Marker (PDF) 
Enable WCP in 2 x DC and 3 x CL


---
layout:     post
title:      "Guest post&#58; EMC and Microsoft Think Big"
date:       2010-06-01 15:49:00
categories: disaster-recovery
---
Hi, I'm Adrian Simays, Hyper-V technical architect at EMC. EMC and Microsoft have been thinking big lately.  How big?  We’ve set out to build and test one of the largest Hyper-V environments in the world.  And why not?  With the release of Windows Server 2008 R2, Microsoft introduced features such as clustered shared volumes (CSVs) for storing multiple VHDs on a single LUN, more efficient processing of networking traffic, as well as improved memory management and support for 256 logical processors.  Meanwhile EMC’s storage arrays are known for delivering unprecedented levels of scalability, availability and performance.  In particular, EMC’s Virtual Provisioning technology saves space and provides high levels of performance, which is something that solutions that tend to use CSVs can benefit from.  Combined, Windows Hyper-V and EMC storage platforms can easily support a large-scale, highly available virtualized configuration.  Plus, here at EMC, we continue to see wide adoption of Hyper-V including large scale deployments (this includes one of our customers who is currently running _seven 16-node Hyper-V clusters on one EMC Symmetrix VMAX_!). So we set out to build a large scale Hyper-V cluster to capture the performance benefits of these new features. The goal of this test is to demonstrate how the environment scales using features made available with Windows Server 2008 R2 and EMC’s Symmetrix VMAX Enterprise Storage Platform.  Objectives for this test were fairly aggressive due to the size and scale of the configuration. We wanted to create 16 nodes in a Windows Failover Cluster with each parent node containing 64 child virtual machines for a total of 1024 virtual machines.  We set out to achieve 100,000 total IOPS and document the hardware layout as well as capture best practices. So what have we found so far?  Well we found that we could exceed our total I/O goal with just 4 parent nodes containing a total of 256 VMs.  By using Live Migration we spread VMs across the parent nodes while leaving the physical data on the CSV volume.  This verified that the underlying storage platform, when appropriately configured can scale as we provide parallel access from multiple nodes in the Active/Active configuration provided with CSV.  We are continuing to collect performance data as we increase the number of parent servers and VMs in the environment. Another key finding included some efficiencies in deploying an environment of this size.  We found that scripting the deployment of VMs using a SCVMM template was extremely easy and took about 15 minutes to deploy 5 VMs over the network (using two 1Gbit network links).  This is great for most environments but for 1024 VMs this would take 52 hours to complete.  By using EMC’s TimeFinder technology and using snapshots, the entire processing time could be significantly reduced to just a few minutes.  A volume was provisioned with Windows images that were configured via SYSPREP.  These images (aka templates) also included required applications.  By creating snapshot copies of the master volume and then importing these replicas as CSVs and finally instantiating the VMs we could reduce the time to create the VMs to a matter of minutes for each parent server. Interested to learn more?  Come join us at Microsoft TechEd 2010 where EMC will present on this solution and the key findings during one of the Breakout Sessions (VIR207: Advanced Storage Infrastructure Best Practices to Enable Ultimate Hyper-V Scalability) as well as a joint whitepaper to be published shortly.  For more information, please visit: [www.emc.com/microsoftvirtualization](http://www.emc.com/microsoftvirtualization).

 Adrian
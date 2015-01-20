---
layout: post
status: publish
published: true
title: The Future, Yesterday
author:
  display_name: VMTyler
  login: vmtyler
  email: me@vmtyler.com
  url: http://vmtyler.com
author_login: vmtyler
author_email: me@vmtyler.com
author_url: http://vmtyler.com
wordpress_id: 59
wordpress_url: "//vmtyler.com/?p=59"
date: '2012-02-19 09:08:23 -0500'
date_gmt: '2012-02-19 14:08:23 -0500'
categories:
- Storage
- Virtualization
tags: []
---
<p>Wow, It's been a while since I've made a post. I'm going to try to post more often. Anyway.</p>
<p><strong>Like VMware , but for storage!</strong></p>
<p>I read a note today from one of EMC's competitors that made me chuckle. It spoke of a "paradigm shift in storage the same way VMware change the x86 server</p>
<p><img class="alignleft  wp-image-76" style="margin:2px;" title="vmotion" src="{{ site.baseurl }}/images/2012/02/vmotion.gif" alt="" width="168" height="158" /></p>
<p>market." Now this isn't the first time I've heard a storage company use the tired "we're like VMware, but for storage!" slogan, but this time it got me thinking.</p>
<p>What this company is really announcing is "we're like ESX2.5, but for storage!" (Not as catchy.) It is the ability to move storage workloads between discrete storage controllers non-disruptively. Manually, no DRS or HA. And any one workload is still bound to the resources in the controller that owns it. A nice feature but not exactly a revolutionary paradigm shift.</p>
<p><strong>Back to the Future</strong></p>
<p>Let me paint you another picture. Some time in the future, VMware announces a new version of vSphere. This new version allows users to truly treat server resources like a pool- you have a total amount of CPU cores, memory, and NICs added up for the whole cluster and you can assign as much or as little as you need. Not limited to the resources of a single vSphere host for a single workload. If I have 2.5TB of memory and 120 cores across my vSphere cluster, I can assign as much as I want to a VM and the vSphere nodes will use a high speed interconnect (like Infiniband or RapidIO) to share all the resources between vSphere hosts.</p>
<p><strong>Sounds amazing, right? But what does VMAX have to do with this?</strong></p>
<p>Well that's pretty much how the Symmetrix VMAX and VMAXe work. Each engine, which contains two controllers (directors) are connected to a Virtual Matrix (hence the name VMAX) that connects all the directors together and allows sharing of resources. I can add more CPU (engines), Memory (cache), or NICs (FC Ports) to my workload (LUN) without an outage and without being constrained by the resources of a single director.</p>
<p><img class="alignleft  wp-image-80" style="border-color:initial;border-style:initial;" title="virtualmatrix" src="{{ site.baseurl }}/images/2012/02/virtualmatrix.png" alt="" width="180" height="179" /></p>
<p><strong>What about DRS &amp; HA? VMAX Availability &amp; Scalability</strong></p>
<p>Because the resources are all shared and the resource control is so fine-grained, it also allows for unmatched fault tolerance and minimized performance degradation during a fault. In any dual controller architecture, a loss of one of the controllers means a 50% loss of potential performance during that fault. Your data may be available, but it might not be useable. In the VMAX world, workloads can be (and should be) assigned resources across many different directors in different engines. This way, any component failure, means just the loss of that component with minimal impact on performance without administrative intervention. This is even more critical as virtualization means continued consolidation. Which basket would you put all your proverbial eggs in?</p>
<p>This architecture also allows me to add additional resources to the VMAX on the fly- I can start with a single engine and add engines, disk, ports, and cache as I grow.</p>
<p><strong>That's all great, but what's it going to cost me?</strong></p>
<p>In my opinion, this is one of the biggest misconceptions around the Symmetrix for years. Yes, some configurations can cost a lot, but as you see by its marketshare plenty of customers see the value. There are also plenty of VMAX configurations that are cost-competitive with dual controller arrays, and depending on the use-case, the VMAX can have a better TCO.</p>
<p>Fully Automated Storage Tiering (FAST VP) has made a huge change here- customers are now buying much more SATA, much less FC, a few EFDs, and letting VMAX sort it out automatically. This has lead to even better TCO.</p>
<p><strong>Enter the VMAXe</strong></p>
<p>The VMAXe has changed this even further- it trims out some features not needed by as many customers (Mainframe support, MASSIVE scale), adds in features customers do want (RecoverPoint replication), and simplified operations (all virtually provisioned, install to first IO in 4 hours).</p>
<p><a href="http://wikibon.org/wiki/v/EMC_and_NetApp_lead_in_VMware_Storage_Integration_Functionality" target="_blank">And of course it has all the VMware integrations of its big brother VMAX </a></p>
<p>Now you can understand why the VMAX and VMAXe are seeing great growth in the storage industry today.</p>
<p>So if and when sometime in the future VMWare announces a new version of vSphere like I described, they can say "like VMAX, but for  server virtualization!"</p>
<p><img class="alignnone size-medium wp-image-83" title="emc-symmetrix-v-max1" src="{{ site.baseurl }}/images/2012/02/emc-symmetrix-v-max11.jpg?w=300" alt="" width="300" height="200" /></p>

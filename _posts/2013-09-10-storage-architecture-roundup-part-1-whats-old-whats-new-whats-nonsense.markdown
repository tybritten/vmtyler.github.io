---
layout: post
status: publish
published: true
title: 'Storage Architecture Roundup (Part 1): What''s Old, What''s New, What''s Nonsense.'
author:
  display_name: VMTyler
  login: vmtyler
  email: me@vmtyler.com
  url: http://vmtyler.com
author_login: vmtyler
author_email: me@vmtyler.com
author_url: http://vmtyler.com
wordpress_id: 182
wordpress_url: "//vmtyler.com/?p=182"
date: '2013-09-10 10:03:13 -0400'
date_gmt: '2013-09-10 14:03:13 -0400'
categories:
- Storage
tags: []
---
<h4>Food for Thought</h4>
<p>While at VMworld last week, besides booth duty, I had some time to stop and visit other vendor booths. It has always been one of my favorite things to do at VMworld- you get to see how the big boys are positioning themselves and what exciting new startups are ready to change the world.</p>
<p>I also was able to sneak into two sessions. The first was the always awesome Bruce Davie and his<a href="https://vmworld2013.activeevents.com/connect/sessionDetail.ww?SESSION_ID=5716" target="_blank"> NET5716 - Advanced VMware NSX Architecture</a> session. I highly recommend watching the recording if you missed it. The second was <a href="http://virtualgeek.typepad.com/virtual_geek/2013/08/vmworld-2013-sto5420sds-the-big-picture.html" target="_blank">Chad's STO5420–SDS </a>session, and one slide he put up really resonated with me, talking about the 3 types of storage architectures. The only change I would make is split the second type into two different ones.</p>
<p style="text-align: center;"><a href="{{ site.baseurl }}/images/2013/09/storage_types.png" target="_blank"><img class="aligncenter size-medium wp-image-206" alt="storage_types" src="{{ site.baseurl }}/images/2013/09/storage_types-300x168.png" width="300" height="168" /></a></p>
<p style="text-align: left;">This really got me thinking. Can we really put all the currently available architectures into one of these four buckets? It really crystallized as I talked to smaller/newer vendors with "new" architectures as they (as most vendors do) highlighted the strengths of their approach and ignored/dismissed the caveats. Chad was right. Almost every single offering, new and old, fit into one of these models. Trying to claim your new product is some incredible paradigm-shifter that doesn't fit into these buckets? Most likely nonsense.</p>
<p style="text-align: left;">In this 3 part series, we'll talk about each of the models, some examples of them, what the engineering trade-offs are that are being made, and what it means for the types of workloads these architectures can handle.</p>
<p>&nbsp;</p>
<h4 style="text-align: left;">The Four Storage Architectures</h4>
<p style="text-align: left;">In Chad's slide above, he names three types. First off, I'm going to set aside <strong>Type 3 (Object storage)</strong>, and focus on the transactional storage models:</p>
<p style="text-align: left;"><strong>Scale Up (Type 1)-</strong> These are your traditional-style dual controller arrays. Scale by adding disks. Think: EMC VNX, NetApp, Pure , Nimble, Compellent, IBM DS8000.</p>
<p style="text-align: left;">As I mentioned, I'm going to split Type 2 into two separate models:</p>
<p style="text-align: left;"><strong>Scale Out (Type 2a)-</strong> This is your modern shared-nothing architecture. Scale by adding nodes, each with processing and storage. Think: EMC Isilon, Nutanix, ScaleIO, IBM XIV, VMware VSAN.</p>
<p style="text-align: left;"><strong>Scale Around (Type 2b)-</strong> This is an older architecture model, but is in use by a couple of younger platforms as well. Scale around is a scale-out architecture that is purposely limited to a finite maximum. Scale is primarily an availability operation instead of a performance one. Scale by adding disks &amp; nodes. Think: EMC VMAX, HP 3Par, HDS VSP.</p>
<p style="text-align: left;">To avoid a <em>War &amp; Peace</em> blog post, I'm going to hit on a two consistent themes and then dedicate a post to each of the above types.</p>
<p>&nbsp;</p>
<h4 style="text-align: left;">The Latency Compass</h4>
<p><a href="{{ site.baseurl }}/images/2013/09/compass.jpg"><img class="wp-image-192 alignleft" style="margin: 8px;" alt="compass" src="{{ site.baseurl }}/images/2013/09/compass.jpg?w=296" width="160" height="162" /></a></p>
<p style="text-align: left;">When measuring a system for performance the only important measurement of latency is cumulative latency. The client asks for an IO- how long does it take to return with the data or acknowledgement for the write? That said, when designing a system you need to measure the latency at all the relevant points to be able to minimize it as much as possible.</p>
<p style="text-align: left;">Designers of High Performance Computing (HPC) clusters refer to two types of latency: East-West latency and North-South latency. East-West is inter-node latency. If your process or job has to talk to other nodes, it's the amount of time it takes to complete that part of the IO. North-South latency is client/node latency. How long from the request at the client until it gets a result from the requesting node.</p>
<p style="text-align: left;">Why are we talking about this here? While storage latency had been defined for years by mainly N/S latency with negligible E/W latency, some of these newer architectures flip this on its head. We'll discuss how it effects each architecture.</p>
<p>&nbsp;</p>
<h4 style="text-align: left;">Do Work Son!</h4>
<p style="text-align: left;"><a href="{{ site.baseurl }}/images/2013/09/969630_589422491090908_1483097656_n.png"><img class="alignright  wp-image-202" style="margin: 8px;" alt="969630_589422491090908_1483097656_n" src="{{ site.baseurl }}/images/2013/09/969630_589422491090908_1483097656_n-257x300.png" width="180" height="210" /></a>One last note on storage arrays- array controllers (software or hardware) are busy beavers. The amount of operations that must be done per client IO have only increased from things like just RAID calculations to now include hashing for dedupe, compression, RAIN ops, replication, snapshots, etc etc.  So not only are modern storage systems doing more client IOPS overall, they're doing more work to complete each of those IOs.</p>
<p style="text-align: left;">Luckily, most array vendors have switched to x86 architecture and <a href="http://en.wikipedia.org/wiki/Moore%27s_law">Moore's Law</a> (and our friends at Intel) has provided leaps in CPU horsepower to handle the additional workload. That said, it's still far from a negligible workload and if you're looking to leverage software or virtual arrays, you will need to add additional (sometimes pretty significant) compute power to handle that workload.</p>
<p>&nbsp;</p>
<h4 style="text-align: left;">Next:</h4>
<p style="text-align: left;"><a title="Storage Architecture Roundup(Part 2): Type 1 Storage- Scale Up" href="//vmtyler.com/storage-architecture-rounduppart-2-type-1-storage-scale-up/">Storage Architecture Roundup(Part 2): Type 1 Storage- Scale Up</a></p>
<p style="text-align: left;"><a title="Storage Architecture Roundup(Part 3): Type 2a Storage- Scale Out" href="//vmtyler.com/storage-architecture-rounduppart-3-type-2a-storage-scale-out/">Storage Architecture Roundup(Part 3): Type 2a Storage- Scale Out</a></p>
<p style="text-align: left;"><a href="//vmtyler.com/storage-architecture-rounduppart-4-type-2b-storage-scale-around-conclusions/">Storage Architecture Roundup(Part 4): Type 2b Storage- Scale Around &amp; Conclusions</a></p>

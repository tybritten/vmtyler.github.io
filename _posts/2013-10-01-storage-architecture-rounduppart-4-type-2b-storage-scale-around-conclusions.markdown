---
layout: post
status: publish
published: true
title: 'Storage Architecture Roundup(Part 4): Type 2b Storage- Scale Around & Conclusions'
author:
  display_name: VMTyler
  login: vmtyler
  email: me@vmtyler.com
  url: http://vmtyler.com
author_login: vmtyler
author_email: me@vmtyler.com
author_url: http://vmtyler.com
wordpress_id: 246
wordpress_url: "//vmtyler.com/?p=246"
date: '2013-10-01 09:29:58 -0400'
date_gmt: '2013-10-01 13:29:58 -0400'
categories:
- Storage
tags: []
---
<p>If you landed on this post, you may want to start with <a title="Storage Architecture Roundup (Part 1): What’s Old, What’s New, What’s Nonsense." href="//vmtyler.com/storage-architecture-roundup-part-1-whats-old-whats-new-whats-nonsense/">Storage Architecture Roundup (Part 1)</a>, <a title="Storage Architecture Roundup(Part 2): Type 1 Storage- Scale Up" href="//vmtyler.com/storage-architecture-rounduppart-2-type-1-storage-scale-up/">Storage Architecture Roundup (Part 2): Type 1 Storage- Scale Up</a>, and <a href="//vmtyler.com/storage-architecture-rounduppart-3-type-2a-storage-scale-out/">Storage Architecture Roundup(Part 3): Type 2a Storage- Scale Out.</a></p>
<h4>Type 2b: Scale Around Storage</h4>
<p style="text-align: left;"><img class="wp-image-273 aligncenter" alt="scale_around" src="{{ site.baseurl }}/images/2013/09/scale_around.png" width="234" height="202" /></p>
<p style="text-align: left;">So to be clear, this is not an accepted industry term. In fact, by googling "Scale Around Storage" it appears no one is using this terminology. So why am I using it here? The more standard terminology for this class of arrays would be the same as type 2a- Scale Out. While it is accurate, these arrays have a significantly different architecture and design considerations that make them different enough from the scale-out systems we already talked about to warrant their own category.</p>
<h5>What about Monolithic, Enterprise, or Mainframe class?</h5>
<p>Yes, some of these arrays have previously been called those names, but there are others (like the IBM DS8000) that has been called all three of those things, but is architecturally a type 1 dual controller array.</p>
<p>&nbsp;</p>
<h4>Client IO Path</h4>
<p>You'll notice the diagrams are similar to the ones from Type 1. The two main differences in the diagrams are:</p>
<ul>
<li>The two controllers displayed can be two of many more controllers (up to 16 on the VMAX).</li>
<li>Inter-controller communications in Type 2b can actually bypass the CPU of the remote controller for higher performance.</li>
</ul>
<p>The Flow of write IOs through a scale around array can vary somewhat, but as an example IO through a VMAX generally goes like this:</p>
<ul>
<li>Client initiates the IO and transmits it across the network (SAN or IP SAN) to the next hop.</li>
<li>The IO flows through all the switch hops and lands on the front end port of one of the controllers.</li>
<li>The controller receives that IO and caches it into global memory in two locations on two different controllers. It access the memory locations directly via the inter-controller link (RapidIO).</li>
<li>Once the controller confirms both writes have been made, it responds back to the client acknowledging the write.</li>
<li>The write is eventually flushed to disk (SSD or Magnetic).</li>
</ul>
<p>&nbsp;</p>
<p><a href="{{ site.baseurl }}/images/2013/09/type2b_io_flow3.png"><img style="border: 0px;" title="type2b_io_flow.png" alt="Type2b io flow" src="{{ site.baseurl }}/images/2013/09/type2b_io_flow3.png" width="480" height="241" border="0" /></a></p>
<p>The flow of read IOs is similar:</p>
<ul>
<li>Client initiates the IO request and transmits it across the network (SAN or IP SAN) to the next hop.</li>
<li>The request flows through all the switch hops and lands on the front end port of one of the controllers.</li>
<li>The controller receives the IO request, checks global memory for the location of the data. If it exists in RAM, it will access the memory location directly via the inter-controller link (RapidIO) no matter which controller physically contains the data.</li>
<li>If the data isn't in global memory, it's a "read miss" and the data is read directly from the underlying disks (flash or magnetic).</li>
<li>The controller places a copy of the read in cache (if it was a "read miss") and responds to the client with the requested data.</li>
</ul>
<h4>Characteristics of Scale Around Arrays</h4>
<p>Positives</p>
<ul>
<li>Inter-controller latency (East/West) is extremely low to the point of being almost negligible.</li>
<li>Up to the maximum performance of the controllers, North/South Latency is dependent mainly on the back-end disks.</li>
<li>Since both N/S and E/W system latency is so low, scale around arrays are great for transactional workloads that max out lower than the system's maximum utilization (&lt;1ms response times possible, read and write)</li>
<li>By limiting the maximum scale and hardware components, these arrays can deliver great transactional performance and at the same time unmatched reliability in comparison to type 1 and 2a arrays.</li>
</ul>
<p>Negatives</p>
<ul>
<li>Scale is limited to the horsepower of the maximum number of controllers (For VMAX, it's 16). Most top out at around 2000-3000 drives.</li>
<li>While some of these systems use x86 architectures, they are delivered in custom hardware packaging. The others use custom ASICs/hardware. This generally causes longer lead times for new technology (CPUs, chipsets)  to make it into these arrays.</li>
</ul>
<p>Failure Domains</p>
<ul>
<li>This is where Type 2b arrays really can shine. The microcode on these arrays can generally allow individual component failures (memory boards, ports, CPU cores, etc.) without having to take the entire controller offline. This resiliency provides higher availability as well as better performance during a fault. This is one of the main reasons customers choose this style of array.</li>
</ul>
<h4>Some Examples</h4>
<ul>
<li>EMC Symmetrix VMAX</li>
<li>HDS VSP</li>
<li>HP 3Par</li>
</ul>
<p>&nbsp;</p>
<h4>Conclusion</h4>
<p>As you may have noticed, I have not called out one architecture as 'the best.' Like most things, there are engineering tradeoffs that are made, resulting in products that are better at some things than others. The real caution I can provide you is if some vendor tells you that they don't fit into any of these categories and they can do everything very well, they're either lying or uninformed themselves.</p>

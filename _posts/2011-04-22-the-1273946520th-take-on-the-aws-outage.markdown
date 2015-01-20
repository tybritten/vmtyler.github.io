---
layout: post
status: publish
published: true
title: The 1,273,946,520th take on the AWS Outage
author:
  display_name: VMTyler
  login: vmtyler
  email: me@vmtyler.com
  url: http://vmtyler.com
author_login: vmtyler
author_email: me@vmtyler.com
author_url: http://vmtyler.com
wordpress_id: 31
wordpress_url: https://vmtyler.wordpress.com/?p=31
date: '2011-04-22 20:58:21 -0400'
date_gmt: '2011-04-23 00:58:21 -0400'
categories:
- Cloud
tags: []
---
<p>Yeah, yeah, yeah. Get your eye rolls out of the way.</p>
<p><em>Oh look, another self-important (insert favorite profanity here), here to tell us what the AWS outage means. It's either:</em><br />
<em> 1. This proves public cloud doesn't work</em><br />
<em> 2. The effect of the outage shows how big cloud is</em><br />
<em> 3. He's here to tell us AWS customers how dumb we are and how if we were on his technology this would have never happened</em><br />
<em> 4. OpenStack would have prevented the outage, cured cancer, and beat Kasperov at Chess</em></p>
<p>Actually, no. I think the outage customers of AWS are experiencing really exposes two key issues:</p>
<p>1. "Cloud" doesn't magically abdicate your responsibilities as an IT department to BC/DR planning and testing. It can be a component of your strategy not your replacement for one.</p>
<p>2. Vendor lock-in is still Vendor lock-in, even in a shiny cloud wrapper.</p>
<p>The key to avoiding vendor lock-in is workload portability- something VMware brought to our own internal data centers. Without portability, IaaS/PaaS is just ASP2.0. This is where our friendly neighborhood open source evangelists jump in and yell "OpenStack!" I personally don't see how taking a <a href="http://en.wikipedia.org/wiki/Harrison_Bergeron">Harrison Bergeron </a>approach to IT infrastructure is good for companies; it's lowest-common-denominator IT. What is key and what vendors and customers should be pushing for is standard APIs and data formats to give us portability without giving up on the decades of intellectual capital that have been poured into things like storage, compute, and networking.</p>
<p>I agree that there is a march towards comoditization- you can see it in the storage industry. Most of the major players are using off the shelf hardware components, but they are innovating in the software layer. Platforms like Engenuity and VNX OE can add a ton of value through features like FAST VP. As long as they are addressable natively by your cloud management platform of choice, what's the problem? Let customers/providers worry about building their stack with the components they deem most valuable, and lets spend our energy on making all those stacks able to talk to each other.</p>

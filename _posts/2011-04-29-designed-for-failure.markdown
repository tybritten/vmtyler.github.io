---
layout: post
status: publish
published: true
title: Designed for failure?
author:
  display_name: VMTyler
  login: vmtyler
  email: me@vmtyler.com
  url: http://vmtyler.com
author_login: vmtyler
author_email: me@vmtyler.com
author_url: http://vmtyler.com
wordpress_id: 37
wordpress_url: "//vmtyler.com/?p=37"
date: '2011-04-29 14:01:25 -0400'
date_gmt: '2011-04-29 18:01:25 -0400'
categories:
- Cloud
tags: []
---
<p><em>Designed for failure.</em></p>
<p>This phrase has been showing up a lot more since the most recent AWS outage. It's a pretty simple concept- your design should expect component failure and be able to deal with it. It's something enterprise organizations have done for years in their <em>infrastructure</em>. The key word there (and why this is getting a lot of press now) is infrastructure. RAID, clustering, redundant networks, load balancers, etc. have been used by service providers and internal IT for years to avoid single points of failure within their infrastructure design, and provide availability for their <em>applications</em>. The applications (for the most part) have <em>not</em> been designed for failure.</p>
<p>Some applications have evolved to add some levels of increased availability (Oracle ADG, Microsoft Exchange DAGs, etc) and some new applications are being written from the ground up to handle all sorts of component failures. A great example (and has been touted frequently) is the Netflix design that leverages <a href="http://techblog.netflix.com/2010/12/5-lessons-weve-learned-using-aws.html">the famed chaos monkey.</a></p>
<p>The problem is, this is the exception not the rule. Most organizations have tons of apps from tons of vendors, and I'm sure some still contain legacy code from punch-card days. It's easier to say "rewrite your apps for the cloud" than it is to actually do it. Even if most of your apps have some level of availability baked in, each one has its own methodology which can be a management nightmare.</p>
<p>This has been one of the driving forces behind virtualization of legacy applications beyond simple consolidation; leveraging the increased availability provided by solutions like VMware HA, DRS, FT, SRM, etc.  This way your creaky old app written with a foxpro back-end can get higher levels of availability. VMware (and it's customers) have been highly successful with this methodology- designing for failure in the infrastructure is cheaper &amp; quicker than rewriting old apps or migrating to new ones.</p>
<p>Commoditization</p>
<p>This dovetails nicely with the previous discussion around hardware commoditization and value added software layers. Hardware is commodity, but your 'availability/designed for failure' secret sauce isn't. If you're Netflix or Google and can put that secret sauce in your software, sure you can use whatever white-box hardware you can buy by the pallet and be fine. But if you're the average enterprise and your apps aren't built that way, well then you're going to need some layer between those dumb disks/cpus that provides that availability. Today those layers are called things like VMware vSphere, EMC Enginuity, VNX OE, and Cisco UCS Manager.</p>

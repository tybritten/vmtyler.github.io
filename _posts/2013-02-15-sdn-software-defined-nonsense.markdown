---
layout: post
status: publish
published: true
title: SDN- Software Defined Nonsense
author:
  display_name: VMTyler
  login: vmtyler
  email: me@vmtyler.com
  url: http://vmtyler.com
author_login: vmtyler
author_email: me@vmtyler.com
author_url: http://vmtyler.com
wordpress_id: 147
wordpress_url: "//vmtyler.com/?p=147"
date: '2013-02-15 10:52:17 -0500'
date_gmt: '2013-02-15 15:52:17 -0500'
categories:
- Virtualization
- Cloud
tags: []
---
<p><strong>It's not what you think it is</strong></p>
<p>Don't worry, this isn't going to be a post explaining how some new buzzword is either complete rubbish marketing or the next great thing. I was having a discussion with a co-worker around the latest term floating around our industry- software-defined datacenters (SDDC). We were debating whether SDDC was the "future" of virtualization, how it fits with cloud, et cetera. I think some good came from those discussions so I figured why not share them here.</p>
<p><strong>Let's Start with Cloud</strong></p>
<p>Not to beat a dead horse, but let's talk about cloud first. I still find <a href="http://www.youtube.com/watch?v=okqLxzWS5R4">Simon Wardley's talk from OSCON '09</a> to still be incredibly relevant here. I agree with his premise that Cloud is mainly talking about an technology operation model, not a technology. Yes, recent technology advances have made this model more feasible, but it's still just a way of doing things.</p>
<p><strong>So what about IT as a Service (ITaaS)?</strong></p>
<p>To me, (whatever) as a service in the IT context is the overlaid business model. ITaaS has existed for quite some time and some companies have adopted it years ago; IT acts as a service provider to the business and charges the business cost centers for resources consumed. Now its only been recently that technology like virtualization has allowed IT to share more resources and charge business units back for much more granular consumption. So ITaaS is not even an operational model, it's the business/financial model that sits on top. It's the IT department taking the IT service provider model and using it internal to the company.</p>
<p><strong>ITaaS leverages Cloud</strong></p>
<p>As i mentioned, companies have been doing (or at least trying) the ITaaS model long before the cloud concept was feasible. What cloud brings the the party is a model which allows providers to deliver service faster, cheaper, and with a better customer experience. This applies to both service providers as well as IT departments working in the ITaaS model.</p>
<p><strong>What about software defined datacenters (SDDC)? Does that replace cloud?</strong></p>
<p>This is where we actually start talking about actual technology. There are two similar but slightly different takes on SDDC:</p>
<p>In the first, the promise of SDDC is that current manageability limitations of physical hardware like network switches, firewalls, and storage arrays can be overcome by separating out the control plane from the data plane. The idea being that moving the control/management to a virtual layer can allow for simpler, more agile operations.</p>
<p>Nicira (the recent VMware acquisition) is a great example of this concept- software defined networking (SDN). It has/had a great fit with very large organizations and service providers that have very complex network topologies that usually include hardware from multiple vendors.  SDN allows all the 'smart' networking to happen completely in software switches and nodes and allows the underlying hardware to be the lowest common denominator and focus on pushing packets with little ongoing reconfiguration. This makes it even easier for orchestration/automation tools to configure networking on the fly via APIs.</p>
<p>The second SDDC methodology is one that has been around a bit longer- the vAppliance. The concept is that both the control and data planes go through a virtual version of what was traditionally physical hardware. This is where VMware vShield Edge firewalls, Avamar Virtual Edition, NetApp's ONTAP Edge virtual storage appliances, and others fit. I can provide multitenant support by just spinning up an additional copy of that vApp for the new tenant.</p>
<p>Obviously under both of these models, the underlying hardware requires less intelligence. The big difference I see is that the first option fits much larger enterprise and service provider environments where the second is tuned for small-medium business (SMB). The net outcome for companies that are trying to operate in a cloud model, SDDC can make that easier by limited touch points for their orchestration/automatic framework of choice.</p>
<p><strong>In Summary</strong></p>
<p>The way I see it:</p>
<p>ITaaS-&gt;Cloud-&gt;SDDC</p>
<p>is</p>
<p>Business-&gt;Operations-&gt;Technical.<br />
Thoughts?</p>

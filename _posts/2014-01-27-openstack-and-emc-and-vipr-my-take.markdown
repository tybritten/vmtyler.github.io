---
layout: post
status: publish
published: true
title: OpenStack and EMC (and ViPR!) - My Take
author_login: vmtyler
author_email: me@vmtyler.com
author_url: http://vmtyler.com
wordpress_id: 335
wordpress_url: "//vmtyler.com/?p=335"
date: '2014-01-27 14:33:46 -0500'
date_gmt: '2014-01-27 19:33:46 -0500'
categories:
- Virtualization
- Cloud
tags: []
---
<h4><strong>UPDATED 9/26/2014 with latest supported driver information</strong></h4>
<h4>A Little Background</h4>
<p>I put up a blog post on the EMC Communities site yesterday<a href="https://community.emc.com/community/connect/everything_vmware/blog/2014/01/27/emc-and-openstack"> outlining EMC's OpenStack support <em><strong>here.</strong></em></a></p>
<h4>A Quick Recap</h4>
<p>More details are available on the above link, but here's the table:</p>

| Array| Supported Release | Protocol | Volume Functions | Location
------------- | ------------- | ------------- | ------------- | ------------- |
| VMAX  | Grizzly, Havana, IceHouse | iSCSI, FC | All required functions, except ‘Create Vol from snapshot’, ‘Extend vol’ | Distribution |
| VNX  | Grizzly, Havana, IceHouse | iSCSI, FC | All required functions | Distribution |
| XtremIO  | Havana, IceHouse | iSCSI | All required functions | GitHub |
| ScaleIO  | Havana, IceHouse | SDS/SDC | All required functions | EMC |
| Ilsion  | Havana, IceHouse | NFS(Cinder) | All required functions | EMC |
| ViPR  | Havana, IceHouse | iSCSI, FC | All required functions | GitHub |

<p>&nbsp;</p>
<h4>My Take</h4>
<p>We announced yesterday the availability of a non-commercial edition of the ViPR controller. That's right, not a time-limited trial, but a fully functioning version. I've waited in anticipation for this version of ViPR to be released, because I think it's particularly relevant to the OpenStack community as it follows a release model that customers in this community are familiar with to (RedHat, Ubuntu).</p>
<p>That said, a common question I hear from OpenStack users is:</p>
<address>If ViPR automates storage provisioning leveraging plug-ins, isn't that what Cinder does? why do I need ViPR?</address>
<p>At the very basic level, they both have an API that you can ask for storage and through plug-ins, that storage will be provisioned from physical arrays. What separates out ViPR is the ability to create virtual arrays and virtual pools of storage made up of multiple different arrays (even from different vendors) but provision them from a single cinder plugin. I can also leverage those same pools for physical servers and VMware environments.  Once the Manila project makes it into incubation and then core, ViPR will be able to provide that single layer of orchestration across heterogeneous clouds, arrays, and protocols.</p>
<p><a href="{{ site.baseurl }}/images/2014/01/ViPR_OpenStack.png"><img class=" wp-image-350 alignleft" src="{{ site.baseurl }}/images/2014/01/ViPR_OpenStack-300x159.png" alt="ViPR_OpenStack" width="381" height="201" /></a></p>
<p>&nbsp;</p>

<p>Why buy ViPR then? Well if you’re looking for EMC Support or you wish to add Object (S3, Swift, Atmos) data services, you’ll need the paid version of ViPR.</p>
<p>If you're interested in getting your hands dirty with ViPR, <a href="http://www.emc.com/getvipr"><strong>here</strong> is the link to download.</a></p>

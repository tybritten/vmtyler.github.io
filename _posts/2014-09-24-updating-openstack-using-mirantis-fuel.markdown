---
layout: post
status: publish
published: true
title: Updating OpenStack using Mirantis Fuel
author:
  display_name: VMTyler
  login: vmtyler
  email: me@vmtyler.com
  url: http://vmtyler.com
author_login: vmtyler
author_email: me@vmtyler.com
author_url: http://vmtyler.com
wordpress_id: 540
wordpress_url: "//vmtyler.com/?p=540"
date: '2014-09-24 08:58:56 -0400'
date_gmt: '2014-09-24 12:58:56 -0400'
categories:
- Uncategorized
tags: []
---
<p>In my lab I’ve been using the Mirantis OpenStack distribution (most recently 5.0.1) since it has a deployment tool called Fuel which makes it really easy to deploy and configure. There’s even a virtualbox script to setup an entire environment on your laptop- <a title="" href="http://samuraiincloud.com/2014/08/13/building-openstack-icehouse-in-virtualbox-in-60-minutes-using-mirantis-fuel-2/" target="_blank">Check out Masa’s post on it here</a>.</p>
<p>Mirantis OpenStack 5.1 was released yesterday with some cool new features:</p>
<ul>
<li>The Fuel Master Node can be upgraded from 5.0.x</li>
<li>Fuel 5.1 can update existing 5.0.x Mirantis OpenStack environments to 5.0.2 (Experimental)</li>
<li>Fuel is now protected by access control</li>
<li>Mirantis OpenStack now deploys the ML2 Open vSwitch plug-in for Neutron</li>
<li>Experimental features must be explicitly enabled for Mirantis OpenStack</li>
<li>The Fuel Master Node can now be backed up and restored</li>
<li>VMware NSX is now supported as a network option</li>
</ul>
<p class="">You’ll see on the list one new experimental feature. That features is to use Fuel to update your OpenStack environment (in this case 5.0.1 to 5.0.2). That’s pretty cool. Let’s give it a try.</p>
<!--more-->
<h3 class="">Upgrade the Fuel Master</h3>
<p class="">The first step is upgrading the fuel master. Go to the Mirantis site and download the upgrade package and get it on your fuel master. (I did a wget right from it, but whatever works). Make sure you have enough disk space on your Fuel Master (mine has 60GB) and put the upgrade package in /var/tmp. Use lrzuntar to uncompress the package. Make sure you have at least 2GB of RAM or it will run out of memory before it finishes.<br />
Next, run the upgrade script:<br />
<img class="full aligncenter" title="" src="{{ site.baseurl }}/images/2014/09/1411562931_thumb.png" alt="" align="middle" /><br />
It will take a while to run. Hopefully at the end you’ll see "INFO 10769 (upgrade) *** UPGRADE DONE SUCCESSFULLY"</p>
<p>Once this is done, if we access the Fuel GUI at http://yourfuelipaddress:8000, you’ll see something you’ve never seen before- a login screen. This is part of the new access control system in 5.1. The default login is admin/admin.<br />
<img class="full aligncenter" title="" src="{{ site.baseurl }}/images/2014/09/1411562926_thumb.png" alt="" align="middle" /></p>
<h1 class="">Enable Experimental Features</h1>
<p class="">Mirantis has focused their efforts on their distribution on making things production-grade. You’ll see native support for controller clustering, various hardening efforts, etc. Included in that approach is hiding new features that are deemed experimental. So we’ll have to enable support for experimental features (like this upgrade we want to try).<br />
back to the fuel master CLI. We’ll need to edit a YAML file and restart some processes.</p>
<p>First step is to edit the YAML file at /etc/fuel/version.yaml and add a line for - experimental</p>
<p><img class="full aligncenter" title="" src="{{ site.baseurl }}/images/2014/09/1411562911_thumb.png" alt="" align="middle" /><br />
after we save this file, we’ll need to restart a few processes:<br />
<img class="full aligncenter" title="" src="{{ site.baseurl }}/images/2014/09/1411562906_thumb.png" alt="" align="middle" /><br />
At this point we’re ready to go.</p>
<h3 class="">Updating OpenStack</h3>
<p>Now when I log into the Fuel GUI, select my existing environment, and select the actions tab, I see a new option:<br />
<img class="full aligncenter" title="" src="{{ site.baseurl }}/images/2014/09/1411562900_thumb.png" alt="" align="middle" />When I select Update, I get the usual ‘Are you sure’ dialog, which I accepted. Now I’m taken back to the previous screen, with a progress bar:<br />
<img class="full aligncenter" title="" src="{{ site.baseurl }}/images/2014/09/1411562895_thumb.png" alt="" align="middle" /><br />
After a few minutes (my environment is only 3 nodes), the update is reported as complete:<br />
<img class="full aligncenter" title="" src="{{ site.baseurl }}/images/2014/09/1411563113_thumb.png" alt="" align="middle" /><br />
Now my Icehouse environment has been updated. Hopefully before long, they’ll support between family upgrades as well (Icehouse to Juno).</p>
<p>&nbsp;</p>

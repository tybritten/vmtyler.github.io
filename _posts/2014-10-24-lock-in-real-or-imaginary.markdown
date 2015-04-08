---
layout: post
status: publish
published: true
comments: true
title: 'Lock-in: Real or Imaginary'
author:
  display_name: VMTyler
  login: vmtyler
  email: me@vmtyler.com
  url: http://vmtyler.com
author_login: vmtyler
author_email: me@vmtyler.com
author_url: http://vmtyler.com
wordpress_id: 578
wordpress_url: https://vmtyler.com/?p=578
date: '2014-10-24 14:34:05 -0400'
date_gmt: '2014-10-24 18:34:05 -0400'
categories:
- Uncategorized
tags: []
---
<p>I've been talking to customers about tech for a number of years and many bring up the term "lock-in." They ask "will this product lock us in?" or "We're choosing to go with solution X because we're not locked in." I've had a few thoughts on this issue that I've shared with customers, but I was spurred into putting this post together by a discussion around <a href="http://www.twitter.com/nigelpoulton">@nigelpoulton's</a> post comparing <a href="http://blog.nigelpoulton.com/vsan-is-no-better-than-a-hw-array/">VSAN and HW arrays</a> where he mentions lock-in.</p>
<p>I posited that this long-feared gremlin of IT <em>doesn't exist, and may never have.</em></p>
<h3>What Really is Lock-in?</h3>
<p>When I ask customers that are concerned about lock-in to explain what they mean, they always respond with something along the lines of "I don't want to be stuck with this later."<br />
Ok, now we're getting somewhere. Usually I can get them to boil it down to a situation where changing isn't feasible due to high cost- either time or money.<br />
That's pretty reasonable, but here are the main problems with how IT people generally think about lock-in:</p>
<ul>
<li>It's expressed as a binary state; you're either locked-in or you're not</li>
<li>The actual costs of being locked-in are never adequately quantified</li>
<li>There's plenty of time and money spent avoiding lock-in but it's generally not quantified</li>
</ul>
<!--more-->
<h3>Friction is the Real Measure</h3>
<p><em>Friction</em> is defined as the resistance to motion; I think this term much better fits the discussion versus the lock-in boogeyman. What we are doing is quantifying (up front, hopefully) what it would cost us in money and time (which is also money) to change something. The higher that cost, the higher the friction. The higher the friction, the higher the benefits of moving need to be to justify. <strong>Every</strong> IT decision creates some level of friction; it's a spectrum.</p>
<p><em>No level of friction is beyond the ability to overcome.</em></p>
<p>Let's look at what's widely considered the most 'locked-in' company-to-technology example we have today- Netflix's platform on AWS. Could Netflix move off of AWS? Absolutely. Would it cost them more than any potential benefits today? Absolutely. As soon as the benefits of re-engineering their platform for another cloud besides AWS outweigh the costs of doing it, they will.</p>
<p>This goes right to the heart of Nigel's comments around VMware VSAN "locking you in to the hypervisor." How much friction is really being created? Definitely some, but is it insurmountable enough to call it lock-in? Hardly.</p>
<h3>Open Source has Friction too</h3>
<p>I also hear people constantly choosing open source projects to avoid the dreaded lock-in. Of course they generally introduce less financial friction, but usually significant time (which costs money) friction to change as well. Choose CloudStack but now want to move to OpenStack? How much work will <em>that</em> be?</p>
<h3>Thinking in Friction and Measuring it Constantly</h3>
<p>Smart IT folks (infrastructure, developers, procurement, and even execs) should be thinking about most decisions this way.<br />
Whether its writing to a specific API, picking a storage platform, or signing a contract they should be asking themselves:</p>
<p><em>How much friction (and what would it cost to overcome) am I introducing to our environment, and is the value we're gaining worth it?</em></p>
<p>There are plenty of examples of companies (like Netflix) making decisions that would be considered locking themselves into a particular technology that are actually really good decisions. EMC moved to SalesForce.com a few years ago and (like most customers) have heavily customized it. I'm sure some would consider EMC locked in to Salesforce, but I bet if we ask EMC Sales leadership, they would make the same decision all over again.</p>
<h3>So does Lock-in exist?</h3>
<p>I guess I would back off saying it doesn't exist at all, but would change the definition of lock-in to <em>a situation where the friction to move outweighs the benefits of moving.</em> If you think in these terms more, you'll stop seeing lock-in hiding in every dark corner.</p>

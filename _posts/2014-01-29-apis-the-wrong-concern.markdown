---
layout: post
status: publish
published: true
title: APIs- The Wrong Concern
author:
  display_name: VMTyler
  login: vmtyler
  email: me@vmtyler.com
  url: http://vmtyler.com
author_login: vmtyler
author_email: me@vmtyler.com
author_url: http://vmtyler.com
wordpress_id: 359
wordpress_url: "//vmtyler.com/?p=359"
date: '2014-01-29 09:14:48 -0500'
date_gmt: '2014-01-29 14:14:48 -0500'
categories:
- Cloud
tags: []
---
<p>I’ve noticed a ton of talk lately about the importance of APIs, and specifically API compatibility. While having properly designed and versioned APIs are critical to anyone looking to increase their automation and orchestration, I think API compatibility is a wildly overblown concern, specifically AWS API compatibility.</p>
<h4>Why AWS API?</h4>
<p>For obvious reasons, the AWS set of APIs (EC2 &amp; S3 mainly) are the set that people are looking for compatibility with because they are the most widely adopted due to the large AWS market share. If your product can deploy using those APIs it can deploy to AWS as well as other compatible clouds (OpenStack, CloudStack, Eucalyptus for example). Conversely, if your cloud platform can support the AWS API set, apps developed to be deployed on AWS will also run on your platform.</p>
<h4>So Where’s the controversy in all this?</h4>
<p>Let me give you a little metaphor:<img class="alignright size-medium wp-image-361" alt="de-dresden-restaurantrow" src="{{ site.baseurl }}/images/2014/01/de-dresden-restaurantrow-284x300.jpg" width="226" height="238" /></p>
<p>In an imaginary little town, there are a bunch of sit-down restaurants. These restaurants generally require reservations, and when you eat there, the chefs come out and meet you and put together a meal based on your likes and dislikes. People generally go to the same restaurant because the chef already knows them and what they like.</p>
<p>A new restaurant opens up in town- the very first fast food restaurant. Customers can order from a very large menu and can also customize their order (extra pickles!). The only problem is the people that work the counter only speak French. People love this exciting new concept for a restaurant- they get exactly what they want, when they want without any reservations or meetings with the chef! Soon people all over town are learning French to be able to order at this new restaurant.</p>
<p>The other res<img class="alignleft size-medium wp-image-363" style="margin: 2px;" alt="13256789-krakow-poland-april-2012-customers-are-buying-fast-food-products-inside-a-kfc-kentucky-fried-chicken" src="{{ site.baseurl }}/images/2014/01/13256789-krakow-poland-april-2012-customers-are-buying-fast-food-products-inside-a-kfc-kentucky-fried-chicken-300x204.jpg" width="218" height="148" />taurants see their business fall pretty dramatically. They hear their customers talking about learning French and ordering at this new place. So what do they do? The owners decide to send all their chefs to French class, but even then, their businesses don’t pick back up. One smart owner decides to revamp his restaurant, modeling it after this new fast food place- but he can’t afford to hire anyone who speaks French. His new counter employees only speak Spanish. To get around that, he publishes a Spanish/French/English menu guide and includes it with the menus. His new restaurant is a hit as well.</p>
<h4>Ok, what does that have to do with APIs?</h4>
<p>Well hopefully you can see the point of the story. The reason this new restaurant was so popular had to do with the completely different consumption paradigm it offered, much like AWS vs traditional IT. The fact that the way you ordered it (API) was a specific language was really a minor detail that can easily be overcome. If the concepts between two cloud services are similar enough, translating the API is relatively minor operation for either the user or the provider. Look how many products and services quickly added  support for one or a bunch of the AWS APIs. For example, pretty much every object storage product or service supports the S3 API.</p>
<h4>So What?</h4>
<p>The main point to me is the actual API doesn’t matter much at all. As long as 1) some sort of robust API exists and 2) the capabilities and concepts the customer needs or are used to using are available, the actual API syntax is an afterthought. More time needs to be spend helping customers change how they consume IT services and change how IT delivers them than worrying about APIs.</p>

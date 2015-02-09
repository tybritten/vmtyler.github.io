---
layout: post
published: true
comments: true
title: 'The Myth of Cloud Economics'
categories:
- Cloud

---
Many pundits assert the inevitability of most workloads eventual moving to a few or single public provider (AWS) due to their size and economies of scale will make both private clouds and smaller public ones financial noncompetitive.

##### Economies of Scale
The reason for this assumption is a basic understanding of the concept of economies of scale; the more you produce, your cost per item decreases.

![chart](/images/2015/01/economyofscale.gif)

It makes logical sense, and this is where the idea that no small cloud provider or private cloud will ever be close to being cost competitive with public cloud giants like AWS.

The problem is, this over-simplistic view doesn't hold true (and actually leaves out half of the graph).

##### Diseconomies of Scale
This is what the graph *actually* looks like:
![chart](/images/2015/01/diseconomyofscale.gif)
There is an equilibrium past where each additional widget you produce *costs more.*

What?

Think about it this way: as an organization grows, it doesn't (and can't) add direct revenue producing investments like production people and equipment; they add managers, and managers of managers, and so on. These additional expenses don't directly produce revenue so they're a cost that is spread across the organization.

I've oversimplified; the actual scale graphs take different shape by company and industry, but they always start going back up.

##### Paradoxical Public Cloud Economic Arguments
This to me is the most interesting phenomenon. Many people make arguments to support their belief of AWS's cost supremacy by highlighting huge investments Amazon has made in areas traditionally adjacent to datacenters and computing. It goes something like this:

*"Amazon is so big, they're buying/building their own [something], which gives them incredible economies of scale! No enterprise can match this scale or cost (even including AWS's margins), so they should get out of the compute business and just move their workloads to AWS."*

For example, Amazon has made investments in the power grid. They've built their own substations, investing in their own generation, etc. While this sounds impressive (and it is), it actually disproves this argument. In this case, individual power companies operate on scale magnitudes greater than Amazon does. If this argument was true, would Amazon be better off leveraging these companies' greater economies of scale and get a lower price by not investing in it directly for their comparatively lower scale.

This was recently revisited with [Amazon's recent acquisition of a networking chip manufacturer](http://www.datacenterknowledge.com/archives/2015/01/23/amazon-buys-stealthy-israeli-chip-startup-annapurna-labs/). While they use a massive amount of networking ports, its still small compared to the number of ports produced by the ODM networking vendors. If unending economies of scale were the immutable law of the universe, why wouldn't they just keep buying switches from Quanta, etc.?

##### The Devil is in the Details
Clearly markets are way more complex than I'm portraying, and *definitely* more complex than portrayed by those expecting AWS (or public clouds in general) to own most of the world's commercial compute resources.

What's the point? The path to more economical cloud environments doesn't only lead to the public cloud. What I've seen is well-run smaller clouds (both public and private) can meet the economics of the larger public clouds. For larger private clouds, they can often offer dramatic savings.
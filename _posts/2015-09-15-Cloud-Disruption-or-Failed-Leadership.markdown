---
layout: post
status: publish
published: true
comments: true
title: 'Cloud Disruption or Failed Leadership?'
categories:
- cloud

---
Watch enough presentations on modern IT and cloud computing and you'll see the same theme over and over. New companies that are Digital/Platform 3/Cloud are disrupting existing industries. The most well-worn examples are Uber, Tesla, and Nest. The takeaway of the presentation is supposed to be that this huge technology advancement is enabling smaller companies to disrupt larger established players and if you want to disrupt/avoid being disrupted, you must embrace these new technologies.

### How to Survive?
Along with the tales of this massive technology disruption to not only IT but businesses as a whole, a frequently cited strategy for overcoming it is 'Bimodal IT.' The premise which is espoused by Gartner, IDC, as well as a number of vendors basically describes an IT department divided into two groups— a group focused on existing 'legacy' IT while a new group needs to be created to design-build-run these new 'cloud-native apps.'
Not only is this concept built on an incorrect understanding of the forces at work, actually trying to implement it is a recipe for disaster.

###  Revolution or Evolution?
As new ideas or products are invented, they start out hard to define hard to predict entities that evolve over time. The more share they gain, the more defined they become.

![](/images/2015/09/diffusion.png)
[Simon Wardley has covered this extensively](http://blog.gardeviance.org/2015/03/evolution-diffusion-hype-cycle-and.html) on his blog and in many talks. It's the march towards ubiquity and utility.

From the perspective of computing, what are we really seeing happen here over the past decade? It's compute moving from being a product that you buy (servers), into services you consume, to a utility that you pay that's metered in hours and minutes. It's a normal technology evolution which was neither unpredicted ([John McCarthy foretold of utility computing in 1961!](https://en.wikipedia.org/wiki/John_McCarthy_(computer_scientist))) nor a dramatic technology advancement to the consumer.


### The Next Age of Compute

If this is a expected normal evolution of computing technology, why are so many companies struggling with it? Cloud computing has brought along another change with it that's really causing the disruption.

Since VAXcluster was released by DEC in 1984, we've been living as an industry in the age of clustered systems. The learning curve in the early days was high and required the best and brightest. As clustered systems became more understood and productized, it was easy to understand and move from things like Microsoft Cluster Services to VMware DRS/HA Clustering. Developers built apps that expected and understood clustering technologies 'just talk to the database at this IP' and infrastructure engineers knew how to build and maintain them.

Cloud computing marks the arrival of the age of distributed systems. It requires significantly advanced skills to both build apps and infrastructure that operate in this manner.

### Skills Shortages are the True Source of the Disruption

Ask any hiring manager working on distributed systems on either the development or infrastructure side and they'll tell you how few candidates there are will the skill sets they need. How did this happen?

### Years of Bad IT Leadership

Let's go back to that chart we started with. How many CIOs in the previous decade put a dot on there called 'IT' and decided it had been pretty much all commoditized, so why not outsource all of it to IBM Global Services or EDS? Or even if they had enough sense to break that dot apart, it was probably only into two dots called 'development' and 'infrastructure', they probably *still* put these two monoliths near the top right. What did they do then? Offshoring, replacing 'expensive' experienced developers, architects and engineers with less experienced, cheaper ones. Now that they need developers and engineers with higher skill levels, they're nowhere to be found.

### Hiring: Must have 10 years Docker Experience

It's amazing to see IT and HR organizations that can't understand why they can't find people with tons of experience in a brand new technology for their set developer/engineer rates, either internally or externally. They've completely forgotten that:

* They've been using offshoring, H-1B visas, and other cost saving measures that have suppressed their pay rates on common technologies and think that applies broadly
* They only pay lip service to personal development and skimp on training and conference attendance budgets.
* They've become so focused on process for process's sake (ITIL, etc.) that anyone they had that could have picked up this new technology quickly is long gone.

And at the same time, a few of their similar sized competitors have had no trouble taking advantage of cloud computing, barely missing a beat. The organizations that are surviving and thriving have a common thread— their teams have discovered and learned these new technologies on their own, they weren't hired in.

**The organizational structure, leadership, inertia, and internal development (or lack thereof) is what's causing disruption not 'The Cloud.'**

### Why Bimodal IT Isn't a Cure

This is why bimodal IT is so nonsensical. Assuming if you decided to split your IT shop into two groups:

1. Where are you going to find the skills you need?
2. Who is going to want to stay in the old organization with the implied scarlet letter of 'you're not as good as those people we chose'?
3. 10 years from now when there is the next new age, do you create a third group? New, Less New, Old? Does the 'old stuff' get handed off to the group that stayed behind? Does the new group become the old group and the old group is fed to lions?

If it is so nonsensical, why is it gaining favor so much? *It's because so many companies want it to be true.* Bimodal tells them 'all the decisions you made up to now were right, and you don't have to make drastic changes, just add a new team to address these new needs.' It provides them with the smallest disruption to their current worldview. [Simon has a great post on Bimodal here, including alternatives.](http://blog.gardeviance.org/2014/11/bimodal-it-is-long-hand-for-snafu.html)

### An IT Wakeup Call

The relatively slow pace of enterprise technology changes over the past decade lulled IT leadership into thinking that this was the norm. Why bother investing in your employees and advancing their skill sets when they could pick incremental new technology in their free time? IT departments were seen as a cost center that had to be controlled and the services IT provided mature and well understood.

It turns out this simple, myopic view of IT and the decisions made based on that view are what's really causing the disruption in Enterprise IT today— not cloud computing.

---
layout: post
published: true
comments: true
title: 'Contributing to OpenStack Documentation'
categories:
- Cloud
- OpenStack
- Open Source

---
Contributing to an open source project can be really rewarding, both as an individual contributor as well as for larger organizations. While I'm going to cover contributing to OpenStack specifically, much of this applies to any open source project.

### Documentation is a Great Way to Start
I highly recommend contributing to documentation for a number of users.

##### End User
If you're an end user, how many times have you tried to install some software and ran into problems and you're told to RTFM and your answer is *"I DID read the docs. They're ambiguous / missing / flat out wrong!"*? Open source projects uniquely give you the ability to *fix* it.

##### Non-Coder
You don't know Python, Golang, Erlang, Ruby, or heck any programming languages. You do like the community aspect of open source and want to help out. Documentation is often neglected and you can give it the attention it deserves.

##### New Contributors
You're actually pretty decent with whatever language your open source project of choice is written in. You've even tweaked it in your own install. You want to start contributing but it seems intimidating. Starting with documentation can help you learn how contributions flow and become part of the community in your project of choice.

#### One Quick Word on Authorization
No, I'm not talking about LDAP or TACACS; I'm talking about *legally*. Even if you wish to contribute on your personal time, if your day job includes working in IT or software, your employer or employment agreement might have some rules specifically about contributing. We're not going to talk about it any more than this mention: check with your company's HR or legal department before you start contributing- code or documentation.

#### OpenStack Contribution Process
Contributing to OpenStack can seem especially daunting to a newcomer as it follows a slightly more complex process. [Here's the full details from the OpenStack Foundation.](https://wiki.openstack.org/wiki/How_To_Contribute) I'll summarize for you (and give you a nice tool to make it even easier).

##### Git, Gerrit, Jenkins & Launchpad

If you're not familiar, here's a quick overview of the tools used by OpenStack to manage development of both code and documentation. If you're already familiar you can skip this part.

[Git](http://git-scm.com/) is a distributed version control system very commonly used in open source projects. [GitHub](http://github.com) is a commercial hosted git repository for collaborating using Git. OpenStack's actively developed code and documentation is hosted there.

[Gerrit](https://code.google.com/p/gerrit/) is a code review tool developed by Google that integrates with Git. It allows testing and review of code before it's committed to a project.

[Jenkins](http://jenkins-ci.org/) is a [continuous integration](http://en.wikipedia.org/wiki/Continuous_integration) (CI) tool. What Jenkins does is automatically build and test code with the proposed changes to make sure it didn't break anything.

[Launchpad](https://launchpad.net/) is a website by Canonical/Ubuntu for collaborating on open source projects. The main use for it in OpenStack is bug tracking.

##### Accounts
Now that you know what the tools are, you'll need a couple of accounts. You'll need to use the same email address for all of them.

* [The OpenStack Foundation](http://www.openstack.org)- You'll want an account anyway, but this is a requirement to contribute. You'll also have to digitally sign the individual contributor agreement.
* [Launchpad](https://launchpad.net/)- Your account here is used as a single-sign-on source for Gerrit as well. Launchpad will generate a username for you, but if you wish to change it, now is the time.
* [Gerrit](https://review.openstack.org)- While it uses your launchpad id to sign you in, you'll need to sign in once to create an account and select a username.

##### SSH Keys
You'll need an SSH key pair to login to Gerrit when syncing your commits. Some best practices are to:

* Generate a key pair specifically for contributing.
* One key pair per computer you're working from. Putting your private key someplace that you can access from multiple machines makes it not private anymore

#### OpenStack Documentation Contribution Setup

#####Software Needed
I've put together a Vagrant setup to make it easy to get started. What you'll need installed is:

* Vagrant 
* [PuTTY and PuTTYgen if you're on Windows](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html) 
* VirtualBox (Or VMware Fusion/Workstation if you like- you'll need a non-free vagrant provider)
* An XML editor of choice. The main OpenStack manuals are written in XML and then compiled when deployed

Once you have these installed, [download my vagrant setup here.](https://github.com/vmtyler/vagrant-openstack-doc-contrib) You can either download the zip file on the right side of the page and extract it locally, or use the git clone link if you have git installed. In the end you should have a folder called vagrant-openstack-docs-contrib.

#####SSH Key Pair
You'll need that SSH key pair now. if you haven't generated it already, you can do that by issuing this command on Mac/Linux:

~~~
ssh-keygen -f id_rsa -t rsa -N ''
~~~

Or if you're on windows, you use PuTTYgen for this. In either case I don't use a passphrase.

once you have your key pair generated, make sure they're named like this and put them in vagrant-openstack-docs-contrib.

~~~
id_rsa
id_rsa.pub
~~~
Once you generate the keys, you need to add the public one (id_rsa.pub) to your account on gerrit:
[https://review.openstack.org/#/settings/ssh-keys](https://review.openstack.org/#/settings/ssh-keys)

##### Gerrit Config
you need to edit the gitconfig.txt file and supply your name, email address and gerrit username:

~~~
[user]
	name = Joe User
	email = username@domain.com

[gitreview]
    username=gerrituser
~~~

##### Starting your Environment
After that, you start this ubuntu VM with running the command from the cli in the folder with the Vagrantfile:

~~~
vagrant up
~~~

What happens is:

* The VM is booted up
* All the prerequisites are installed
* Your SSH keys are installed
* The git repository for the openstack manuals is cloned locally
* git review is setup with your gerrit account

Your local git repository is stored in /vagrant on the ubuntu machine so it means it is available in the vagrant-openstack-docs-contrib/openstack-manuals directory. 

You're now ready to contribute!

#### Time to Contribute!

You can [check out this link ](https://wiki.openstack.org/wiki/Documentation/HowTo/FirstTimers) for the first-timer instructions from the OpenStack Foundation, but I'm going to go through the key parts here.

##### Bugs
A bug is anything (code or documentation) that doesn't work as expected. In the case of documentation this could be confusing sentences, incorrect command syntax, or something that's outdated or just plain wrong. The only way to keep track of who is working on what is to use the [bug tracker on launchpad.](https://bugs.launchpad.net/openstack-manuals/)
At this point you can either submit a bug for some problem you've found in the documentation, or select an existing bug that isn't already being worked on.

**Bug Terminology**

Bugs have an importance (Low, High, Critical) and a status (new, confirmed, in process, fix committed, triaged, etc.) They are also tagged. What we're going to do now is look for a bug that isn't already being worked (it's new or confirmed) and has the tag 'low-hanging-fruit.' This tag is assigned to bugs that are considered 'easy to fix.'

Once you find a bug that is something you can fix, read the comments and see what suggested fixes are there, if anyone has started working on it, etc. Look at the date of the last assignment to see if someone else just picked it up. If no, take ownership of it by clicking on the little yellow circle under "Assigned" next to the name of who it's currently assigned to.(or unassigned) 
Now that bug is yours. Congrats! Take note of the bug number.

##### Your First Branch
To be able to work on the same project at the same time, git has the concept of branches- you're going to create your own branch to track the changes your making.

Access your ubuntu vm by running this command in the vagrant-openstack-docs-contrib directory:

~~~
vagrant ssh
~~~
You'll now be sshed into the vm- unless you're on Windows. There's a few extra steps:

* convert the %USERPROFILE%\\.vagrant.d\insecure_private_key to .ppk using PuTTYGen
* use the .ppk key in your PuTTY session - configured in Connection > SSH > Auth > Private key file
* use host 127.0.0.1
* use port 2222 instead of 22
* you can set the default username (vagrant) under Connection > SSH > Auth > Private key for authentication

Change directory into /vagrant/openstack-manuals. From now on any commands we run from the VM will be done from this directory.

Create a branch to work on your bug- where nnnnnn is the bug number:

~~~
 	git checkout -b fix-bug-nnnnnn
~~~
You're now ready to start editing the docs. Open the XML file for the document you're contributing to in your vagrant-openstack-docs-contrib/openstack-manuals folder with your XML editor of choice. Make sure to follow the XML formatting guidelines [here.](https://wiki.openstack.org/wiki/Documentation/HowTo)

After you are done editing the docs, you'll want to run the tests to make sure you didn't make any formatting mistakes. From the Ubuntu VM run this command:

~~~
 	tox -v
~~~

If all the tests come back ok, you're ready to commit. If not, read the error messages and see what needs to be fixed. Usually it's a space in the wrong place. To start your commit process, you need to first commit the change locally by typing:

~~~
 	git commit -a
~~~
You end up inside the nano editor where you're now putting your commit message in. [Here are the guidelines](https://wiki.openstack.org/wiki/GitCommitMessages) to properly format commit messages, but the keys are:

* The first line should be a quick summary of the change
* Empty
* Next a detailed summary of the change (if needed)
* Empty Line
* Identify the bug it fixes:

~~~
Closes-Bug: #nnnnnnn
~~~
Then press Ctrl-X to exit and say yes to save.
Now it's time to push your commit up to gerrit by typing:

~~~
 	git review -v
~~~
It should output a url to your change where you can see it in gerrit that's formatted like this:

~~~
https://review.openstack.org/xxxxxxx/
~~~
Note: the gerrit change number will not match the bug id.
Visit the URL and see your change in the system. Within a few minutes, Jenkins will automatically grab your patch set and test it. If your patch passed the local tox test, it should pass Jenkins too. If not, you can see the logs from Jenkins to see why it failed.

#### Review, Verified, Workflow
Once it passes the Jenkins tests, Jenkins should give your change a +1 for Verified. This is the first thing your change needs to have. After that your patch won't be added to the project until you get two +2 from core reviewers.

##### -1? What the Heck?
Sometimes reviewers will suggest changes to your patch set and you'll see their comment with a -1 rating. Don't take it personal. This is the reviewer's way of saying "I don't think this patch is ready yet."

##### Updating Your Patch
Most changes don't get accepted on the first patch set. Let's say you got some really good feedback from a reviewer about your patch and you wish to make that change. All you do is go back to your editor, make the change requested, and then commit it again.
The only difference is you'll this command instead:

~~~
git commit -a --amend
git review -v
~~~
This lets you amend your previous commit and uploads a new patch set to your change.

##### What if you started working on another bug in the meantime?
You can have multiple simultaneous edits going on at the same time, even locally (yay git!). All you need to do is checkout the branch you want to work on. This is why naming the branches after the bug id makes it easy. You'll just run the checkout command before editing.

~~~
 	git checkout -b fix-bug-nnnnnn
~~~
Remember, this is your bug ID, not your patch id from gerrit.

##### Timing
Don't expect your change to be approved immediately. Most changes spend days waiting to be approved, and if you include the changes that you'll invariably need to make to your patch set, it could spend weeks in the system.

##### Stackalytics
Some engineers from Mirantis put together a tool called [Stackalytics](http://stackalytics.com/) that collects contribution data (Commits, Reviews, etc) and charts it by every way imaginable (by contributor, company, project, release. etc). As soon as you start having some activity in gerrit, your information will show up on Stackalytics.

#### Where to Next?

This should be enough to get you started. Once you get the hang of it, you'll see it's not that hard. There are plenty of great resources to learn and troubleshoot if you have issues.

If you are interested in contributing code, most of the process you learned here is identical.  I'm actually working on a similar setup with Vagrant and devstack to streamline that process as well. The only difference is you'll need a Python IDE instead of an XML editor.


#### Wow You Must Contribute a Lot!
Actually, if you check my stackalytics page, you'll see very little activity (so far). I recently received the OK to contribute and struggled a little getting started which is why I put this information together. 

##### Well-seasoned Contributors That Don't Like Something They've Read Above
If you find any of the information provided above isn't accurate enough, good news- this blog is hosted on GitHub Pages and this particular post is [here.](https://github.com/vmtyler/vmtyler.github.io/blob/master/_posts/2015-03-16-contributing-to-openstack-documentation.markdown) Don't hesitate to submit a PR on this post with the changes you recommend. I just ask that you leave the existing text in via a strikeout so someone can see what's new.
---
layout: post
status: publish
published: true
title: AppleScript Markdown-Ready Screenshots
author:
  display_name: VMTyler
  login: vmtyler
  email: me@vmtyler.com
  url: http://vmtyler.com
author_login: vmtyler
author_email: me@vmtyler.com
author_url: http://vmtyler.com
wordpress_id: 465
wordpress_url: "//vmtyler.com/?p=465"
date: '2014-09-10 20:02:57 -0400'
date_gmt: '2014-09-11 00:02:57 -0400'
categories:
- Uncategorized
tags: []
---
<p>So I’ve been putting together a number of documents that include screenshots and I’ve never had a really good way of &nbsp;speeding up the process- take screen shot, insert file into document, etc.</p>
<p>Especially since I started using MacDown as a Markdown editor, I needed to provide the path to the file as well. So here’s my solution- Apple Automator.<br />
Open Apple Automator and create a new service. Search for Run AppleScript and Drag and Drop it into the right so it added to the service.<br />
<img class="full aligncenter" title="" src="{{ site.baseurl }}/images/2014/09/1410393472_thumb.png" alt="" align="middle" /></p>
<p>Paste in the following AppeScript. You can modify it to suit your needs. I have it set it use “-s” to screen shot an area I select. I also have it set to save the files into the screenshot folder inside my dropbox. At the end you’ll see it takes the complete file path and adds the markdown image syntax ![]() to it as well and copies it to the clipboard.</p>

~~~applescript
on run {input, parameters}
	
	set homeFolderPath to POSIX path of (path to home folder as string)
	set screenshotStoragePath to homeFolderPath & "Dropbox/Screenshots/"
	set timeStamp to do shell script "date '+%Y-%m-%d at %I.%M.%S %p'"
	set screenshotFilePath to screenshotStoragePath & "Screen Shot " & timeStamp & ".png"
	do shell script "screencapture " & "-s" & " " & quoted form of screenshotFilePath
	set markdownpath to "![](" & screenshotFilePath & ")"
	set the clipboard to markdownpath
		return input
end run
~~~

<p>Once you save the created service, go to the system preference pane, select keyboard and under shortcuts, find your service and assign a hotkey to it.</p>
<p>Now any time I press that hotkey combo, It takes a screenshot, saves it to my dropbox, and copies the location in markdown to my clipboard.</p>

---
layout: single
author_profile: true
title:  "If you use a Mac, Automator is your friend"
date:   2018-09-19 09:18:00 -0600
categories: mac custom application
header:
  image: /assets/images/posts/using-automator/using-automator.png
  teaser: /assets/images/posts/using-automator/using-automator.png
---
If you use a Mac to do repetitive actions on a daily basis and you don't know what Automator is, you are about to have your mind blown. At least, that's how I felt when I was first introduced to Automator. The best part is that there is no download necessary! It comes with MacOS as a default application.

Automator allows you to create custom scripts, applications, and workflows to help you be productive.

I didn't like that when I sat down to program, I had to open my text editor, start my React Development Server (npm start), and start my Express server (using nodemon). Sure, it's faster to do all of that through the command line. But I couldn't type it all fast enough to prevent my default browser or my text editor from opening before I was done typing all of those commands. On average, I think it would take about 20-45 seconds to get logged in and start working.

Enter Automator. I wrote this script.

```
on run {input, parameters}

	tell application "Terminal"
		if not (exists window 1) then reopen
		activate
		do script "cd path/to/project" in window 1
		tell application "System Events"
			keystroke "t" using {command down}
			keystroke "t" using {command down}
			delay .2
		end tell
		do script "cd react-app" in window 1
		do script "npm start" in window 1
		do script "cd server" in window 2
		do script "nodemon" in window 2
		do script "atom ." in window 3
	end tell

	return input
end run
```

It's nothing super fancy. I haven't even added in a check to see if terminal is already running something. But as of this morning, it had opened terminal and run those commands in less than 2 seconds. Huge time saver.

A former employer used Automator to rename image files to the correct format. In 5-10 seconds he could have his thousands of images renamed and ready to upload to his server.

I've only scratched the surface here, but it makes for a pretty neat trick! What have you done using Automator?
